# ``Đây là quy tắt được lưu hành nội bộ Cty CP Hcosface``  

1. Naming Convention (nói về cái tên biến trước)  
- Tên biến đại khái là cụm từ đơn giản dễ hiểu ngay khi đọc vào và không quá trừ tượng để khó hiểu. Ít nhất khi đặt vào ngữ cảnh của 1 phương thức nào đó tên biến phải mô tả được chức năng của nó hoặc giá trị của nó được dùng để làm gì trong phương thức.  
**Ex:** Tôi lấy vài cái tên trừu tượng ở đây.  
```java
int number = 0; 	// vấn đề ở đây là number gì?
```
Thay vào đó thử xem:
```java
int numberQuestion = 0;
```
Điều trên cho thấy biến `numberQuestion` nó bao hàm cho tôi ý nghĩa là số câu hỏi và không trừu tượng cho người đọc code là số gì?  
- Tránh đặt tên khó hiểu rồi comment. Tôi lấy ví dụ ở trên nếu `int number = 0;` rồi sau đó comment vào như sau:
```java
// number of question
int number = 0;
```
đó không phải là cách mà thay vào đó hãy đặt tên biến 1 cách rõ ràng.  
- Không được viết sai chính tả để tránh việc hiểu sai ý nghĩa của tên biến. 
- Sử dụng rõ ràng tên của biến ra. Ví dụ: thay sử dụng dụng `get` hãy sử dụng `fetch`, `download` tùy vào ngữ cảnh.
- Tránh dùng những tên chung chung như `tmp`, `retval` trừ khi đó là cách cuối cùng.
- Khi sử dụng biến có kiểu dữ liệu `boolean` hãy chú ý một số điều sau:
    - Tốt nhất nên tránh sử dụng tên biến mà có nội dung phủ định ví dụ như sau: thay vì dùng `boolean disableSsl = false;`
    thì hãy sử dụng `boolean useSsl = true;`
    - Sử dụng tên biến rõ ràng để biết nó là biến kiểu `boolean`. Ví dụ: thay vì sử dụng `boolean readPassword = true;`
    thì hãy sử dụng `boolean needPassword = true;`
    - Nên thêm vào các tiền tố cho biến `boolean` như: `need`, `is`, `should`, `has`, `can` sẽ giúp cho biến rõ nghĩa hơn.
- Tên biến phải viết theo nguyên tắt camelCase. Và bắt đầu tên biết phải có ít nhất là 2 ký tự a - z lower case đầu tiên. [a-z]
**Ex:** Tôi lấy vài cái tên không đúng quy tắt tôi vừa nói trên ở đây:
```java
 /* 
 Việc sử dụng i ở đây ngụ ý người ta sử dụng muốn chỉ nó ra là kiểu int nhưng nó không thực sự cần thiết.
 */
int iNumberQuestion = 0;
/*
Ở đây việc sử dụng _t sẽ không phù hợp với quy tắt đã được nhắc đến ở trên.
*/
students.forEach(_t -> {
	// do something
})
```
- Tôi có 1 vài gợi ý cho bạn ở đây:
```java
int numberStudent = 0;

students.forEach(student -> {
	// do something
})
```
 - Biến hằng toàn cục là biến phải được upper case toàn bộ và dùng quy tắt SNACK_CASE và sử dụng `keyword` `final`.  
```java
private static final int FETCH_NUMBER = 0;
```
biến toàn cục trên phải là field của class vừa định nghĩa.
**Ex:** Biến toàn cục nằm trong class và đứng trước constructor.
```java
public class Foo {
	private static final int MAX_LENGTH_QUESTION = 8; // biến hằng toàn cục private.
	public static final String QUESTION_QUIZ_TYPE = "QUIZ"; // biến hằng toàn cục public.
	public Foo() { }
}
```
 - Biến cục bộ phải được sử dụng trong 3 lệnh (statement) kế tiếp trong hàm. 
**Ex:** Biến được sử dụng trong lệnh thứ 3 trong phương thức `bar`.  Lệnh `if else` cũng được gọi là 1 statement.
```java
public class Foo {
	public void bar() {
		int totalMark = 0;
		
		if (...) {
		
		}
		
		doSomeThing();
		
		this.checkMark(totalMark, ...); // here valid
	}
}
```
 - Trong tên biến không tồn tại hơn 2 ký tự UPPER CASE liên tiếp.  
**Ex:** Tôi ví dụ cho bạn 1 vài tên khá chuối mà bạn nên tránh như:
```java
int numberCPL = 0; // trong trường hợp này người dùng muốn mô tả number char per line
```
thay vào đó tôi có 1 gợi ý nhỏ cho bạn sẽ ổn hơn trong trường hợp này để không mắc phải quy tắt trên.
```java
int numberCharPerLine = 0; // nó sẽ tốt hơn cho việc đọc hiểu biến này ở đây? bạn có thắc mắc khi đọc tên biến này?
```
 - Đừng để trong source code của bạn xuất hiện những giá trị `magic` nhé. Giá trị magic những số hoặc chuỗi mà dường như không có ý nghĩa trong source code về mặt ngữ nghĩa và nó sẽ làm cho việc đọc code hoặc bảo trì code khó khăn. 
**Ex:** Ví dụ sau tôi sẽ cho bạn thấy nếu xuất hiện số magic trong source sẽ khiến chính bạn sau 1 thời gian đọc lại code của mình cũng khó chịu đấy:
```java
if (paymentMethod == 1) { // số này là gì đây? 1 là gì?
	// process payment
}
```
ví dụ trên cũng có thể có bạn sẽ xử lý như sau:
```java
if (paymentMethod == 1) { // CREDIT
	// process payment
}
```
điều trên nó sẽ đúng tại nơi bạn đang xử lý trên nhưng đến khi bạn vào phương thức khác mà cần sử dụng lại Payment Method CREDIT thì lúc đó source code sẽ xuất hiện nhiều comment như trên lắm đấy.  
**Ex:** 1 Ví dụ nữa để bạn hiểu hơn về khái niệm giá trị `magic`
```java
public class Foo {
	public void setPassword(String password) {
		// don't do this
		if (password.length() > 7) {
			throw new InvalidArgumentException("password");
		}
	}
}
```
Tôi sẽ chỉ cho bạn 2 cách để khắc phục điều trên nhỏ thôi nhưng bạn sẽ phải thốt lên rằng. "Oh!!! That like a charm" 
 - Sử dụng Enum để đặt ra các giá trị vào nhóm Enum như sau:
 ```java
public enum PaymentMethod {
	CREDIT, DEBIT, CASH, CHECK
}
 ```
 lúc đó ví dụ trên của bạn sẽ như thế này: 
 ```java
if (paymentMethod == PaymentMethod.CREDIT) {
	// process payment
}
 ```
 - Sử dụng static global constant:
```java
public class Foo {
    public static final int MAX_PASSWORD_SIZE = 7;
    public void setPassword(String password) {
         if (password.length() > MAX_PASSWORD_SIZE) {
              throw new InvalidArgumentException("password");
         }
    }
}
```
 - Tên thuộc tính cũng được áp dụng tương tự như tên của biến với một số lưu ý cần phải quan tâm.
	- Không được đặt tên trùng lại với tên class (pojo, dto, domain class)
	**Ex:** Class Company sau đây sẽ khiến bạn khó chịu nếu vi phạm quy tắt trên tôi vừa nói đấy
```java
public class Company {
	private String companyName;  // liệu có nên sử dụng tên như thế này cho một thuộc tính của class?
	private String companyId; // như thế này 
	private String companyCode; // và cả như thế này nữa
	...
}
Company company = new Company();
company.getCompanyName();  // cố gắng đừng để xuất hiện điều như thế này trong source của bạn nhé.
```
	hãy đặt như thế này sẽ tốt hơn cho ngữ nghĩa và dễ chịu khi đọc tên biến.
```java
public class Company {
	private String name; 
	private String id; 
	private String code;
	// ...
}
```
```java
Company company = new Company();
company.getName();  // khi đặt đúng quy tắt trên có lẽ bạn đã dễ chịu hơn khi đọc rồi chứ.
```
- Sử dụng thuộc tính của class thì nên kèm theo theo thêm chi tiết đáng chú ý kèm theo tên biến nó sẽ không phải khiến cho 1 ngày nào đó chính bạn phải hỏi câu sau với biến: `int totalTimeExam` đơn vị tính của thuộc tính này là giây hay phút đây nhỉ? Thử lại với cách này xem: `totalTimeExamSec` dài nhỉ? Nhưng sẽ khiến bạn bất ngờ về thông tin bạn biết về nó đấy.

2. Method name(Nói về tên phương thức)  
- Tên phương thức phải được bắt đầu bằng ký tự thường (lowerCase) và sử dụng camelCase.  
**Ex:** 
```java
public class Student {
    public List<Student> findById(String id) {
        // doSomething();
    }
}
```
- Tên phương thức phải đại diện cho một hành động được thực hiện bởi đối tượng. Tên phương thức phải là động từ.
- Tên phương thức phải mang hàm ý là thực hiện hành động thuộc đối tượng đang chứa nó. 
**Ex:**  
```java
public class Car {

	public void run() { // xe thì để chạy

	}

	public void swim() { // xe bơi chăng? sau này thì có thể đấy nhưng bây giờ thì không nên

	}

}
```
- Tên phương thức trả về kiểu dữ liệu boolean thì nên chứa các từ như sau: `has`, `is`, `can`, ...



3. Khoảng trắng trong source code:
- Sử dụng Tab 2 và 2 space để sử dụng trong việc format code có thể hiển thị space char để dễ nhìn khoảng trắng. Có thể dễ dàng cấu hình tab trên bằng cách sử dụng IDE hoặc plug in EditorConfig với file cấu hình .editorconfig sẽ được đính kèm sau đây.
```json
root = true
[*]
charset = utf-8
end_of_line = cr
indent_size = 2
indent_style = space
insert_final_newline = true
max_line_length = 100
tab_width = 2
trim_trailing_whitespace = true
```
- Khi xuống dòng phải sử dụng eol là CR không được phép sử dụng các loại khác như LF hoặc không sử dụng hỗn tạp CRLF.
- Độ dài của 1 dòng không được vượt quá 100 ký tự bao gồm luôn cả Comment inline, comment Block, comment java doc. Để chú ý điều này có thể nhìn vào position của cursor hiện tại.
- Khi xuống dòng tiếp theo của dòng trên dài quá 100 ký tự thì khi xuống dòng phải lùi vào 2 tab so với dòng trên. Có thể cấu hình bằng cách thêm properties vào .configeditor để nó tự hổ trợ khi xuống dòng lùi vô 2 tab như sau:  
```properties
ij_continuation_indent_size = 4
```
**Ex:**: Ví dụ dưới đây dài hơn 100 ký tự vì nó vượt qua vạch line 100 được quy định trong editorconfig.
```java
class Foo {
	public String method(String variable1, String variable2, String variable3, String variable4, String variable5) { // Tôi không nhắc đến việc sử dụng tên biến ở đây. Nó sẽ được đề cập vào phần sau.
	
	}
}
```
- Khi viết query JPQL, HQL, SQL, PLSQL  
	+ Nối chuỗi phải được tuân theo quy tắt 100 char trên 1 line và nếu khi xuống dòng thì phải lùi vào 2 tab và đặt dấu + chuỗi phía trước và cách dấu chuỗi 1 space. 
	+ Khi SQL viết đến WHERE mà có AND thì AND phải được xuống dòng và lùi vào 1 tab, OR có thể để trên 1 dòng và phải có cặp ngoặc tròn `()` để tránh tình trạng nhầm biểu thức hoặc khó đọc cho người review code, viết sau.
	+ SELECT lồng phải được viết ở dòng kế tiếp nhưng dấu mở ngoặc tròn `(` lồng phải được ở dòng trên. Kết thúc dấu đóng ngoặc tròn `)` lồng phải được kết thúc ở hàng mới. Ví xem ví dụ phía dưới.
**Ex:**: Ví dụ như sau
```java
@Query("SELECT m "
    + "FROM HcosYtTypeQuestion m "
    + "WHERE m.companyId = :companyId AND m.status = :status "
    + "ORDER BY m.position ASC, m.updatedAt DESC")
List<HcosYtTypeQuestion> findAllByCompanyId(@Param("companyId") String companyId,
											@Param("status") String status);
```
Ví dụ câu truy vấn lồng
```java
```
- Khi thực hiện bằng format của tài liệu này có thể trình format của IDE sẽ phá hủy quy tắt này đi. Lúc đó có thể sử dụng dấu bỏ qua format của IDE được cấu hình bằng tay hoặc cấu hình mặc định của Intellij IDEA là: `@formatter:off`. Cấu hình bằng cách vào `File | Settings | Editor | Code Style | Formatter Control` check vào dấu Enable formatter markers in comments. Mặc định IDE sẽ dùng `@formatter:off` để bỏ qua việc việt format lại đoạn code nằm trong cặp marker trên. Hoặc có cách khác là có thể dùng .editorconfig cho Intellij IDEA để cấu hình override lên cấu hình của IDE bằng cách thêm các lệnh sau: 
```properties
ij_formatter_off_tag = @formatter:off
ij_formatter_on_tag = @formatter:on
```
**Ex:** Ví dụ trong block `@formatter:off` `@formatter:on` sẽ không được IDE format dù cho là format tự động hay là được gọi lệnh format.
```java
// @formatter:off
String formulaGenerateCode =
    (String) configService.fetchValueConfig(CODE_CONFIG_FORMULA_GENERATE_CODE_TOPIC,
        companyId, DEFAULT_CODE_TOPIC_FORMULA);
String code = CodeHelper.generateCode(
    () -> this.countTotalTopic(companyId),
    formulaGenerateCode,
    (codeValidate) -> this.hasExistTopicCodeCompany(null, codeValidate, companyId));
// @formatter:on
```
- Mỗi file không được vượt quá 1000 line nếu đủ 1000 thì phải chia nhỏ chức năng của file đó ra. Nếu trường hợp không thể thực hiện chia nhỏ phải hỏi ý kiến của `PM` hoặc `Trưởng bộ phận` hoặc `người hướng dẫn trực tiếp`.
- Mỗi phương thức chỉ nên tồn tại 10 statement. Nếu hơn thì chia nhỏ ra và để ý đến khả năng tái sử dụng của code.
4. IDE:
- IDE được sử dụng phải là Intellij IDEA Ultimate phiên bản từ 2018.1 trở lên.
- Không sử dụng các Plugin có kết nối đến hệ thống bên ngoài ví dụ như: TagMyCode, CodeStream, ...
- Khi install plugin phải để ý đến các chi tiết của Plugin nói nằm tránh việc source code bị lấy và public thành các file code template online.
- Khuyến khích sử dụng keymap của VimIdea nằm tăng tốc độ thao tác với source code (plugin mô phỏng VIM Editor).
- Khuyến khích sử dụng Snippet để giảm số code hoặc tính năng phải nhớ.
- Nên sử dụng IDEA Checkstyle để check các style tương tự như quy định trong tài liệu này.
- Phải Install Plugin Lombok để đọc code có sử dụng Lombok.
5. Java:
- Phiên bản Java được sử dụng hiện nay là: **Oracle Java 8 (Java SE 8u221)** để ý không được nâng lên Java 9 hay 11 vì sẽ khác cấu trúc dẫn đến source code không chạy được. Vì Java 9 > có cấu trúc Module khác hoàn toàn với Java 8.
- Phiên bản Maven được sử dụng hiện này là: **3.5.x**
- Phiên bản Framework Spring Boot được sử dụng hiện nay là: **2.1.x** 
- Phiên bản Spring Cloud được sử dụng hiện nay là: **Greenwich.M3**
- Phiên bản Springfox Swagger sử dụng hiện nay là: **2.9.x**
- Các phiên bản trên sẽ nâng cấp đồng loạt vào thời gian tương ứng nếu không có sự thay đổi phiên bản được thông báo từ `Trưởng bộ phận` thì các project phải được sử dụng các phiên bản tương tự và không có sự nâng cấp không được cho phép nào của `Trưởng bộ phận`.


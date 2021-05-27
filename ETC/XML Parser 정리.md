------

# XML PARSER 비교 분석

●  XML 파서의 종류   <BR>

● DOM <BR>

● SAX <br>

● STAX <br>

● JAXB 


------

## ***\*💡\** XML이란 무엇인가요?

●  XML은 HTML과 매우 비슷한 문자 기반의 마크업 언어(text-based markup language)입니다.
이 언어는 사람과 기계가 동시에 읽기 편한 구조로 되어 있습니다. <br>

● XML은 HTML처럼 데이터를 보여주는 목적이 아닌, 데이터를 저장하고 전달할 목적으로만 만들어졌습니다.<br>

●  XML 태그는 HTML 태그처럼 미리 정의되어 있지 않고, 사용자가 직접 정의할 수 있습니다. <br>


<h5> XML의 특징 </h5>

1. XML은 다른 목적의 마크업 언어를 만드는 데 사용되는 다목적 마크업 언어입니다.<br>

2. 다양한 종류의 데이터를 손쉽게 교환할 수 있도록 해줍니다.  <br>

3. XML은 새로운 태그를 만들어 추가해도 계속해서 동작하므로, 확장성이 좋습니다.  <br>

4.  데이터를 보여주지 않고,  데이터를 전달하고 저장하는 것만을 목적으로 합니다.<br>
 
5. 텍스트 데이터 형식의 언어로 모든  XML 문서는 유니코드 문자로만 이루어집니다.<br>

```
참고) XML 표준사이트 <br>
-https://www.w3.org/TR/xml/
```

------

## ***\*💡\**XML PARSER  

<h5> 1) DOM Parser</h5>

  ● 처음 xml 문서를 메모리에 모두 로드한 후 값을 읽는다. <br>

  ● xml문서가 메모리에 모두 로드되어있기 때문에 노드의 검색, 수정,  구조변경등이 빠르고 용이하다. <br>

  ● 직관적이고 SAX보다 파싱하기 단순하다.<BR>
  
 ```
 ● DomParser 접근방법
 
File file = new File("test.xml");

DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();

DocumentBuilder db = dbf.newDocumentBuilder();

Document doc = db.parse(file);
```

  
  <H6>● DOM 파서 구현 <br></H6>


 ```
doc.getDocumentElement().normalize();

String rootName = doc.getDocumentElement().getNodeName(); //루트 엘리먼트의 이름을 리턴 합니다.

NodeList nodeLst = doc.getElementsByTagName("region_id"); //문서에서 region_id 노드를 전부 찾아 배열로 돌려줍니다.

Node fstNode = nodeLst.item(0); //nodeList의 첫번째 노드를 추출 합니다.

Element fstElmnt = (Element) fstNode;

NodeList fstNmElmntLst = fstElmnt.getElementsByTagName("announce_date");

//fstElmnt의 하위에 announce_date태그 네임을 검색하여 배열로 돌려 줍니다

Element fstNmElmnt = (Element) fstNmElmntLst.item(0); ////fstNmElmntList의 첫번째 노드를 추출 합니다.

NodeList fstNm = fstNmElmnt.getChildNodes(); //fstNmElmnt의 하위 노드들 추출

System.out.println("URL : "+ ((Node) fstNm.item(0)).getNodeValue()); //첫번째 노드의 값 출력

 위와 같이 getElementsByTagName() 과 getNodeValue()같은 함수를 사용하여 노드를 검색하고 값을 뽑아냅니다.

```

  

<h5> 2) SAX Parser</h5>

● xml 문서를 순차적으로 읽어들이면서 노드가 열리고 닫히는 과정에서 이벤트가 발생한다.<br>

  ● xml문서를 메모리에 전부 로딩하고 파싱하는것이 아니라서 메모리 사용량이 적고 단순히 읽기만 할 때 속도가 빠름.<br>

  ● 발생한 이벤트를 핸들링하여 변수에 저장, 활용하는 것이기 때문에 복잡하고, 노드 수정이 어렵다.<br>

  ● Dom보다 어렵다. <br>
  

```
● SAXParser 접근방법

SAXParser parser = SAXParserFactory.newInstance().newSAXParser();

File xmlFile = newFile(“test.xml”);

parser.parse(xmlFile, new SAXSampleParser());

```




<h6> SAXParer 파싱 방법 </h6>

```
클래스 선언에서 DefaultHandler를 상속받아 아래 함수들을 오버라이드 하여 사용해야 한다.

  // 문서의 시작시 발생하는 이벤트 입니다.

  public void startDocument() throws SAXException {

    super.startDocument();

  }

  

  // 파서가 xml을 읽는 도중 엘리먼트 시작테그를 만날 때마다 발생하는 이벤트

  public void startElement(String uri, String localName, String qName, Attributes attributes) throws SAXException {

 //qName 엘리먼트의 이름

// 엘리먼트 속성

    for (int i = 0; i < attributes.getLength(); i++) {

      //System.out.println(“Attribute: ” + attributes.getQName(i) + “=” + attributes.getValue(i));

    }

  }

  

  // 엘리먼트 끝

  public void endElement(String uri, String localName, String qName) throws SAXException {

    //System.out.println(“End Element: ” + qName);

  }

  

  // 엘리먼트 이벤트 중간중간 텍스트를 만났을때 발생

  public void characters(char ch[], int start, int length) throws SAXException {

    //System.out.println(“Character: ” + new String(ch, start, length));

  }

  

  // 문서의 끝

  public void endDocument() throws SAXException {

    super.endDocument();

    System.out.println(“End Document”);

  }

위와 같이 SAX방식은 이벤트 발생시마다 호출 되는 함수에 제어할 구문을 구현하여 사용하여야 한다.
```

## ***\*💡\**STAX PARSER  

<h5> 1) STAX Parser</h5>

  ● SAX, DOM의 장점을 보완한 파서 API 모델 <br>

  ● StAX는 push와 pull 방식을 동시에 제공하는 하이브리드한 형태입니다. <br>

  ● JAXB보다 속도는 느리지만, 메모리 소모가 적은 경우 사용합니다.<BR>
  
 ```
 ● DomParser 접근방법
 
File file = new File("test.xml");

DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();

DocumentBuilder db = dbf.newDocumentBuilder();

Document doc = db.parse(file);
```

  
  <H6>● DOM 파서 구현 <br></H6>


 ```
//stax 파서를 사용한 코드
public class XmlSTAXReader {

	public static void main(String[] args) {

		String fileName = "C:\\FileIO\\book.xml";

		Long startTime = System.currentTimeMillis();

		List<Book> bookList = parseXML(fileName);

		Long endTime = System.currentTimeMillis();

		for (Book book : bookList) {
			System.out.println(book.toString().trim());
		}
		System.out.println("실행시간 : " + (endTime - startTime) + "ms");

	}

	private static List<Book> parseXML(String fileName) {
		List<Book> bookList = new ArrayList<Book>();
		boolean isWriter = true;
		Book book = null;
		XMLInputFactory xmlInputFactory = XMLInputFactory.newInstance();
		try {
			XMLEventReader xmlEventReader = xmlInputFactory.createXMLEventReader(new FileInputStream(fileName));
			while (xmlEventReader.hasNext()) {
				XMLEvent xmlEvent = xmlEventReader.nextEvent();
				if (xmlEvent.isStartElement()) {
					StartElement startElement = xmlEvent.asStartElement();
					if (startElement.getName().getLocalPart().equals("code")) {
						book = new Book();
						Attribute idAttr = startElement.getAttributeByName(new QName("id"));
						if (idAttr != null) {
							book.setId(Integer.parseInt(idAttr.getValue()));
						}
					} else if (startElement.getName().getLocalPart().equals("name")) {
						xmlEvent = xmlEventReader.nextEvent();
						if (isWriter) {
							book.setName(xmlEvent.asCharacters().getData());
							isWriter = false;
						} else {
							book.setWname(xmlEvent.asCharacters().getData());
							isWriter = true;
						}
					} else if (startElement.getName().getLocalPart().equals("rank")) {
						xmlEvent = xmlEventReader.nextEvent();
						book.setRank(xmlEvent.asCharacters().getData());
					} else if (startElement.getName().getLocalPart().equals("price")) {
						Attribute idAttr = startElement.getAttributeByName(new QName("won"));
						if (idAttr != null) {
							book.setPrice(Integer.parseInt(idAttr.getValue()));
						}
					} else if (startElement.getName().getLocalPart().equals("sale")) {
						xmlEvent = xmlEventReader.nextEvent();
						book.setSale(xmlEvent.asCharacters().getData());
					}
				}
				if (xmlEvent.isEndElement()) {
					EndElement endElement = xmlEvent.asEndElement();
					if (endElement.getName().getLocalPart().equals("code")) {
						bookList.add(book);
					}
				}
			}
		} catch (FileNotFoundException | XMLStreamException e) {
			e.printStackTrace();
		}
		return bookList;
	}

}

```

-Book.xml의 구조 -
```
<?xml version="1.0" encoding="UTF-8"?>
<book>
    <code id="0">
        <name>TEST0</name>
        <writer>
            <name>dymgaqhyuo</name>
            <rank>j</rank>
        </writer>
        <price won="63000">
            <sale>n</sale>
        </price>
    </code>
    <code id="1">
        <name>TEST1</name>
        <writer>
            <name>hskrohzlwj</name>
            <rank>p</rank>
        </writer>
        <price won="29000">
            <sale>y</sale>
        </price>
    </code>
    <code id="2">
        <name>TEST2</name>
        <writer>
        ...
        ...
        ...
        ....
        .....
```




# Referece

● http://tcpschool.com/xml/xml_intro_basic

● https://developer.mozilla.org/ko/docs/Web/API/DOMParser

● https://humble.tistory.com/23
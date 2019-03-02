---
title: Wczesne i późne wiązania (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'early binding [Visual Basic]'
  - 'objects [Visual Basic], late-bound'
  - 'objects [Visual Basic], early-bound'
  - 'objects [Visual Basic], late bound'
  - 'early binding [Visual Basic], Visual Basic compiler'
  - 'binding [Visual Basic], late and early'
  - 'objects [Visual Basic], early bound'
  - 'Visual Basic compiler, early and late binding'
  - 'late binding [Visual Basic]'
  - 'late binding [Visual Basic], Visual Basic compiler'
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
---
# <a name="early-and-late-binding-visual-basic"></a>Wczesne i późne wiązania (Visual Basic)
Kompilator języka Visual Basic wykonuje w procesie zwanym `binding` gdy obiekt jest przypisany do zmiennej obiektu. Obiekt jest *z wczesnym wiązaniem* gdy jest przypisany do zmiennej zadeklarowany typ określonego obiektu. Wczesne obiektów powiązanych umożliwić kompilatorowi przydzielić pamięci i wykonywać inne optymalizacje, przed wykonaniem aplikacji. Na przykład poniższy fragment kodu deklaruje zmienną typu <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Ponieważ <xref:System.IO.FileStream> jest określonego typu obiektu, wystąpienie, przypisany do `FS` jest z wczesnym wiązaniem.  
  
 Z drugiej strony, obiekt jest *Rozpoznanie późnego wiązania* gdy jest przypisany do zmiennej zadeklarowane jako typu `Object`. Obiekty tego typu może przechowują odwołania do dowolnego obiektu, ale nie ma wiele korzyści wynikające z wczesnym wiązaniem obiektów. Na przykład poniższy fragment kodu deklaruje zmienną obiektu obiektu zwróconego przez `CreateObject` funkcji:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Korzyści wynikające z wczesne powiązania  
 Obiekty wczesnym wiązaniem, jeśli to możliwe, należy użyć, ponieważ umożliwiają one kompilator udostępnia ważne optymalizacje, które bardziej wydajne aplikacje. Obiekty z wczesnym wiązaniem są znacznie szybsze niż obiektów z późnym wiązaniem i uczynić kod łatwiejszym do odczytywania i obsługa poprzez podanie dokładnie jakiego rodzaju obiektów są używane. Inną zaletą wczesne powiązania jest umożliwienie przydatne funkcje, takie jak uzupełnianie kodu automatyczne i dynamiczna pomoc ponieważ Visual Studio zintegrowane środowisko programistyczne (IDE) można określić dokładnie typ obiektu pracujesz w trakcie edycji Kod. Wczesne powiązania ogranicza liczby i ważności błędów czasu wykonywania, ponieważ umożliwia kompilatorowi raportowanie błędów, gdy program jest kompilowany.  
  
> [!NOTE]
>  Rozpoznanie późnego wiązania należy używać tylko na dostęp do elementów członkowskich typu, które są zadeklarowane jako `Public`. Uzyskiwanie dostępu do elementów zadeklarowane jako `Friend` lub `Protected Friend` powoduje błąd w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)

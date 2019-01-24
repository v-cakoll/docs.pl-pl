---
title: Wczesne i późne powiązania (Visual Basic)
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
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="fcc94-102">Wczesne i późne powiązania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcc94-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="fcc94-103">Kompilator języka Visual Basic wykonuje w procesie zwanym `binding` gdy obiekt jest przypisany do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="fcc94-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="fcc94-104">Obiekt jest *z wczesnym wiązaniem* gdy jest przypisany do zmiennej zadeklarowany typ określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fcc94-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="fcc94-105">Wczesne obiektów powiązanych umożliwić kompilatorowi przydzielić pamięci i wykonywać inne optymalizacje, przed wykonaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fcc94-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="fcc94-106">Na przykład poniższy fragment kodu deklaruje zmienną typu <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="fcc94-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 <span data-ttu-id="fcc94-107">Ponieważ <xref:System.IO.FileStream> jest określonego typu obiektu, wystąpienie, przypisany do `FS` jest z wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="fcc94-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="fcc94-108">Z drugiej strony, obiekt jest *Rozpoznanie późnego wiązania* gdy jest przypisany do zmiennej zadeklarowane jako typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="fcc94-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="fcc94-109">Obiekty tego typu może przechowują odwołania do dowolnego obiektu, ale nie ma wiele korzyści wynikające z wczesnym wiązaniem obiektów.</span><span class="sxs-lookup"><span data-stu-id="fcc94-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="fcc94-110">Na przykład poniższy fragment kodu deklaruje zmienną obiektu obiektu zwróconego przez `CreateObject` funkcji:</span><span class="sxs-lookup"><span data-stu-id="fcc94-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="fcc94-111">Korzyści wynikające z wczesne powiązania</span><span class="sxs-lookup"><span data-stu-id="fcc94-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="fcc94-112">Obiekty wczesnym wiązaniem, jeśli to możliwe, należy użyć, ponieważ umożliwiają one kompilator udostępnia ważne optymalizacje, które bardziej wydajne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="fcc94-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="fcc94-113">Obiekty z wczesnym wiązaniem są znacznie szybsze niż obiektów z późnym wiązaniem i uczynić kod łatwiejszym do odczytywania i obsługa poprzez podanie dokładnie jakiego rodzaju obiektów są używane.</span><span class="sxs-lookup"><span data-stu-id="fcc94-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="fcc94-114">Inną zaletą wczesne powiązania jest umożliwienie przydatne funkcje, takie jak uzupełnianie kodu automatyczne i dynamiczna pomoc ponieważ Visual Studio zintegrowane środowisko programistyczne (IDE) można określić dokładnie typ obiektu pracujesz w trakcie edycji Kod.</span><span class="sxs-lookup"><span data-stu-id="fcc94-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="fcc94-115">Wczesne powiązania ogranicza liczby i ważności błędów czasu wykonywania, ponieważ umożliwia kompilatorowi raportowanie błędów, gdy program jest kompilowany.</span><span class="sxs-lookup"><span data-stu-id="fcc94-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc94-116">Rozpoznanie późnego wiązania należy używać tylko na dostęp do elementów członkowskich typu, które są zadeklarowane jako `Public`.</span><span class="sxs-lookup"><span data-stu-id="fcc94-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="fcc94-117">Uzyskiwanie dostępu do elementów zadeklarowane jako `Friend` lub `Protected Friend` powoduje błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fcc94-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc94-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcc94-118">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="fcc94-119">Okres istnienia obiektów: Jak obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="fcc94-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="fcc94-120">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="fcc94-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

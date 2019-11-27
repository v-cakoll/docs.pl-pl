---
title: Wczesne i późne wiązania
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: bd70d8642c18e9bc2baba8128ec908c88e0477ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345184"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="53591-102">Wczesne i późne wiązania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53591-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="53591-103">Kompilator Visual Basic wykonuje proces o nazwie `binding`, gdy obiekt jest przypisany do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="53591-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="53591-104">Obiekt jest *wczesnie powiązany* , gdy jest przypisany do zmiennej zadeklarowanej jako określonego typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="53591-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="53591-105">Obiekty wczesnych powiązań umożliwiają kompilatorowi przydzielanie pamięci i wykonywanie innych optymalizacji przed wykonaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="53591-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="53591-106">Na przykład poniższy fragment kodu deklaruje zmienną do typu <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="53591-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="53591-107">Ponieważ <xref:System.IO.FileStream> jest określonym typem obiektu, wystąpienie przypisane do `FS` jest wczesnie powiązane.</span><span class="sxs-lookup"><span data-stu-id="53591-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="53591-108">Z kolei obiekt jest *późnie powiązany* , gdy jest przypisany do zmiennej zadeklarowanej jako typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="53591-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="53591-109">Obiekty tego typu mogą zawierać odwołania do dowolnego obiektu, ale nie wiele zalet obiektów wczesnych powiązań.</span><span class="sxs-lookup"><span data-stu-id="53591-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="53591-110">Na przykład poniższy fragment kodu deklaruje zmienną obiektu do przechowywania obiektu zwróconego przez funkcję `CreateObject`:</span><span class="sxs-lookup"><span data-stu-id="53591-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="53591-111">Zalety wczesnego wiązania</span><span class="sxs-lookup"><span data-stu-id="53591-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="53591-112">Jeśli jest to możliwe, należy używać obiektów wczesnych powiązań, ponieważ umożliwiają kompilatorowi wykonywanie ważnych optymalizacji, które dają wydajniejsze aplikacje.</span><span class="sxs-lookup"><span data-stu-id="53591-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="53591-113">Obiekty wczesnie powiązane są znacznie szybsze niż obiekty z późnym wiązaniem i ułatwiają odczytywanie i konserwowanie kodu przez poznanie tego, jakiego rodzaju obiekty są używane.</span><span class="sxs-lookup"><span data-stu-id="53591-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="53591-114">Kolejną zaletą wczesnych powiązań jest umożliwienie korzystania z użytecznych funkcji, takich jak automatyczne uzupełnianie kodu i Pomoc dynamiczna, ponieważ zintegrowane środowisko programistyczne (IDE) programu Visual Studio może dokładnie określić typ obiektu, z którym pracujesz podczas edycji kodu.</span><span class="sxs-lookup"><span data-stu-id="53591-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="53591-115">Wczesne powiązanie zmniejsza liczbę i ważność błędów czasu wykonywania, ponieważ umożliwia kompilatorowi raportowanie błędów podczas kompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="53591-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53591-116">Późne wiązanie może być używane tylko w celu uzyskania dostępu do elementów członkowskich typu, które są zadeklarowane jako `Public`.</span><span class="sxs-lookup"><span data-stu-id="53591-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="53591-117">Uzyskiwanie dostępu do elementów członkowskich zadeklarowanych jako `Friend` lub `Protected Friend` powoduje błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="53591-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53591-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53591-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="53591-119">Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="53591-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="53591-120">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="53591-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

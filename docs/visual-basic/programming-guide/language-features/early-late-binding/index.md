---
title: Wczesne i późne powiązania (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa63a250ce6bdf4a8a34d9f1c0284a9d04e75f38
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="758d2-102">Wczesne i późne powiązania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="758d2-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="758d2-103">Kompilator Visual Basic wykonuje w procesie nazywanym `binding` gdy obiekt jest przypisany do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="758d2-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="758d2-104">Obiekt *z wczesnym wiązaniem* zadeklarowany gdy jest przypisany do zmiennej typu określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="758d2-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="758d2-105">Wczesne obiektów powiązanych Zezwalaj kompilatora można przydzielić pamięci i wykonywać inne optymalizacje przed wykonaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="758d2-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="758d2-106">Na przykład poniższy fragment kodu deklaruje zmienną typu <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="758d2-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 <span data-ttu-id="758d2-107">Ponieważ <xref:System.IO.FileStream> jest określonego typu obiektu, wystąpienia przypisany do `FS` jest z wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="758d2-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="758d2-108">Z kolei jest obiekt *Rozpoznanie późnego wiązania* zadeklarowany gdy jest przypisany do zmiennej typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="758d2-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="758d2-109">Obiekty tego typu można przechowywania odwołań do dowolnego obiektu, ale nie mają wiele zalet obiektów z wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="758d2-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="758d2-110">Na przykład poniższy fragment kodu deklaruje zmienną obiektu do przechowywania obiektu zwróconego przez `CreateObject` funkcji:</span><span class="sxs-lookup"><span data-stu-id="758d2-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="758d2-111">Zalety wczesne powiązania</span><span class="sxs-lookup"><span data-stu-id="758d2-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="758d2-112">Obiekty z wczesnym wiązaniem, jeśli to możliwe, należy użyć, ponieważ umożliwiają one kompilator w celu optymalizacji ważne, które zwracają większą wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="758d2-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="758d2-113">Z wczesnym wiązaniem obiekty są znacznie szybsze niż obiekty z późnym wiązaniem i upewnij kodu łatwiej odczytywać i obsługa poprzez podanie dokładnie jakiego rodzaju obiektów są używane.</span><span class="sxs-lookup"><span data-stu-id="758d2-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="758d2-114">Inną zaletą do wczesnego wiązania jest przydatne funkcje, takie jak uzupełnianie kodu automatyczne i Pomoc dynamiczna ponieważ Visual Studio zintegrowane środowisko programistyczne (IDE) można określić dokładnie typ obiektu pracujesz w trakcie edycji Kod.</span><span class="sxs-lookup"><span data-stu-id="758d2-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="758d2-115">Wczesne powiązania ogranicza liczbę i ważność błędów czasu wykonywania, ponieważ umożliwia kompilatorowi przesłania raportów o błędach, gdy program ma być kompilowana.</span><span class="sxs-lookup"><span data-stu-id="758d2-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="758d2-116">Późne wiązanie tylko umożliwia dostęp do elementów członkowskich typu, które są zadeklarowane jako `Public`.</span><span class="sxs-lookup"><span data-stu-id="758d2-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="758d2-117">Uzyskiwanie dostępu do elementów członkowskich zadeklarowany jako `Friend` lub `Protected Friend` powoduje błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="758d2-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="758d2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="758d2-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [<span data-ttu-id="758d2-119">Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="758d2-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [<span data-ttu-id="758d2-120">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="758d2-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

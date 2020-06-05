---
title: Nazwa „<name>" nie została zadeklarowana
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 6fa4639b97e4314d8752ae520e94a58a189b7cbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397171"
---
# <a name="name-name-is-not-declared"></a><span data-ttu-id="34549-102">Nazwa „\<name>" nie została zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="34549-102">Name '\<name>' is not declared</span></span>
<span data-ttu-id="34549-103">Instrukcja odwołuje się do elementu programistycznego, ale kompilator nie może odnaleźć elementu o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="34549-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="34549-104">**Identyfikator błędu:** BC30451</span><span class="sxs-lookup"><span data-stu-id="34549-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="34549-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="34549-105">To correct this error</span></span>  
  
1. <span data-ttu-id="34549-106">Sprawdź pisownię nazwy w instrukcji odwołującej.</span><span class="sxs-lookup"><span data-stu-id="34549-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="34549-107">W Visual Basic nie jest rozróżniana wielkość liter, ale każda inna zmiana pisowni jest traktowana jako zupełnie inna nazwa.</span><span class="sxs-lookup"><span data-stu-id="34549-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="34549-108">Należy zauważyć, że podkreślenie ( `_` ) jest częścią nazwy i w związku z tym jest częścią pisowni.</span><span class="sxs-lookup"><span data-stu-id="34549-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2. <span data-ttu-id="34549-109">Sprawdź, czy masz operator dostępu do elementu członkowskiego ( `.` ) między obiektem a jego składową.</span><span class="sxs-lookup"><span data-stu-id="34549-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="34549-110">Na przykład jeśli masz <xref:System.Windows.Forms.TextBox> kontrolkę o nazwie `TextBox1` , aby uzyskać dostęp do jej właściwości, należy <xref:System.Windows.Forms.TextBoxBase.Text%2A> wpisać `TextBox1.Text` .</span><span class="sxs-lookup"><span data-stu-id="34549-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="34549-111">Jeśli zamiast tego wpiszesz `TextBox1Text` , utworzona zostanie inna nazwa.</span><span class="sxs-lookup"><span data-stu-id="34549-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3. <span data-ttu-id="34549-112">Jeśli pisownia jest poprawna i składnia dowolnego dostępu do elementu członkowskiego obiektu jest poprawna, sprawdź, czy element został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="34549-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="34549-113">Aby uzyskać więcej informacji, zobacz [elementy zadeklarowane](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="34549-113">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4. <span data-ttu-id="34549-114">Jeśli element programowania został zadeklarowany, sprawdź, czy znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="34549-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="34549-115">Jeśli instrukcja odwołująca znajduje się poza regionem deklarującym element programowania, może być konieczne zakwalifikowanie nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="34549-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="34549-116">Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="34549-116">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>  

5. <span data-ttu-id="34549-117">Jeśli nie używasz w pełni kwalifikowanego typu lub typu i nazwy elementu członkowskiego (na przykład kod odwołuje się do właściwości jako " `MethodInfo.Name` zamiast" `System.Reflection.MethodInfo.Name` ), Dodaj [instrukcję Imports](../statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="34549-117">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="34549-118">Jeśli próbujesz skompilować projekt w stylu zestawu SDK (projekt z \* plikiem. vbproj, który zaczyna się od wiersza `<Project Sdk="Microsoft.NET.Sdk">` ), a komunikat o błędzie dotyczy typu lub elementu członkowskiego zestawu Microsoft. VisualBasic. dll, skonfiguruj aplikację do kompilowania z odwołaniem do biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34549-118">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="34549-119">Domyślnie podzestaw biblioteki jest osadzony w zestawie w projekcie w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="34549-119">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="34549-120">Na przykład następujący przykład nie zostanie skompilowany, ponieważ <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> nie można odnaleźć metody.</span><span class="sxs-lookup"><span data-stu-id="34549-120">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="34549-121">Nie jest on osadzony w podzbiorze środowiska uruchomieniowego Visual Basic dołączonego do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34549-121">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   <span data-ttu-id="34549-122">Aby rozwiązać ten problem, Dodaj `<VBRuntime>Default</VBRuntime>` element do `<PropertyGroup>` sekcji projekty, jak pokazano w poniższym pliku projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34549-122">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="34549-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34549-123">See also</span></span>

- [<span data-ttu-id="34549-124">Deklaracje i stałe — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="34549-124">Declarations and Constants Summary</span></span>](../keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="34549-125">Visual Basic — Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="34549-125">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="34549-126">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="34549-126">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="34549-127">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="34549-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

---
title: Nazwa „<name>" nie została zadeklarowana
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 3aadc49f91021409123550ba2712f1acf5b99d83
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260147"
---
# <a name="name-name-is-not-declared"></a><span data-ttu-id="96836-102">Nazwa "\<name >' nie jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="96836-102">Name '\<name>' is not declared</span></span>
<span data-ttu-id="96836-103">Oświadczenie odnosi się do elementu programistycznego, ale kompilator nie może odnaleźć element o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="96836-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="96836-104">**Identyfikator błędu:** BC30451</span><span class="sxs-lookup"><span data-stu-id="96836-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96836-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="96836-105">To correct this error</span></span>  
  
1. <span data-ttu-id="96836-106">Sprawdź pisownię nazwy w instrukcji odwołujących się.</span><span class="sxs-lookup"><span data-stu-id="96836-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="96836-107">Visual Basic jest rozróżniana wielkość liter, ale inne zmienność pisowni jest traktowany jako całkowicie inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="96836-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="96836-108">Należy pamiętać, że znak podkreślenia (`_`) jest częścią nazwy i w związku z tym część pisownię.</span><span class="sxs-lookup"><span data-stu-id="96836-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2. <span data-ttu-id="96836-109">Sprawdź, czy operator dostępu do elementu członkowskiego (`.`) między obiektem i jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="96836-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="96836-110">Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formantu o nazwie `TextBox1`, aby uzyskać dostęp do jego <xref:System.Windows.Forms.TextBoxBase.Text%2A> właściwość, należy wpisać `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="96836-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="96836-111">Jeśli zamiast tego wpisz `TextBox1Text`, utworzono inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="96836-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3. <span data-ttu-id="96836-112">Jeśli składnia dostęp do dowolnego obiektu elementu członkowskiego jest poprawna Pisownia jest poprawna, sprawdź, czy element został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="96836-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="96836-113">Aby uzyskać więcej informacji, zobacz [zadeklarowane elementy](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="96836-113">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4. <span data-ttu-id="96836-114">Jeśli zadeklarowano elementu programistycznego, sprawdź, czy są w zakresie.</span><span class="sxs-lookup"><span data-stu-id="96836-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="96836-115">W przypadku instrukcji odwołujących się poza regionem deklarowania elementu programistycznego, może być konieczne kwalifikowania nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="96836-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="96836-116">Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="96836-116">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>  

5. <span data-ttu-id="96836-117">Jeśli nie używasz w pełni kwalifikowany typ lub nazwa typów i elementów członkowskich (na przykład kod odwołuje się do właściwości jako `MethodInfo.Name` zamiast `System.Reflection.MethodInfo.Name`), Dodaj [Imports — instrukcja](../statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="96836-117">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="96836-118">Jeśli chcesz skompilować projekt w stylu zestawu SDK (projektu za pomocą \*pliku .vbproj, który rozpoczyna się od wiersza `<Project Sdk="Microsoft.NET.Sdk">`), a komunikat o błędzie, który odwołuje się do typu lub elementu członkowskiego w zestawie Microsoft.VisualBasic.dll, umożliwia skonfigurowanie aplikacji Skompiluj z odwołaniem do biblioteki środowiska uruchomieniowego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="96836-118">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="96836-119">Domyślnie podzbiór biblioteki jest osadzony w swoim zestawie, w projekcie zestawu SDK stylu.</span><span class="sxs-lookup"><span data-stu-id="96836-119">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="96836-120">Na przykład, poniższy przykład nie powiedzie się do kompilacji ponieważ <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> nie można odnaleźć metody.</span><span class="sxs-lookup"><span data-stu-id="96836-120">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="96836-121">Nie jest zagnieżdżony w podzbiorze środowiska uruchomieniowego Visual Basic, dołączone do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="96836-121">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   <span data-ttu-id="96836-122">Aby rozwiązać ten błąd, należy dodać `<VBRuntime>Default</VBRuntime>` element do projektów `<PropertyGroup>` sekcji, co ilustruje poniższy plik projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="96836-122">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="96836-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96836-123">See also</span></span>

- [<span data-ttu-id="96836-124">Deklaracje i stałe — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="96836-124">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="96836-125">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="96836-125">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="96836-126">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="96836-126">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="96836-127">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="96836-127">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

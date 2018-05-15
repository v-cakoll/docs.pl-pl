---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b64372d4b6063da85739e939bb33abd4650ecb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-doc"></a><span data-ttu-id="cccf7-102">-doc</span><span class="sxs-lookup"><span data-stu-id="cccf7-102">-doc</span></span>
<span data-ttu-id="cccf7-103">Przetwarza komentarzy do dokumentacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="cccf7-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cccf7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cccf7-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="cccf7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cccf7-105">Arguments</span></span>  
  
|<span data-ttu-id="cccf7-106">Termin</span><span class="sxs-lookup"><span data-stu-id="cccf7-106">Term</span></span>|<span data-ttu-id="cccf7-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="cccf7-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="cccf7-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="cccf7-108">`+` &#124; `-`</span></span>|<span data-ttu-id="cccf7-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cccf7-109">Optional.</span></span> <span data-ttu-id="cccf7-110">Określanie +, lub po prostu `-doc`, powoduje, że kompilator, aby wygenerować informacje dokumentacji i umieść go w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="cccf7-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="cccf7-111">Określanie `-` jest odpowiednikiem nieokreślenie `-doc`, powoduje żadne informacje dokumentacji nie ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="cccf7-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="cccf7-112">Jeśli wymagane `-doc:` jest używany.</span><span class="sxs-lookup"><span data-stu-id="cccf7-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="cccf7-113">Określa wyjściowego pliku XML, który jest wypełniana komentarze z plików kodu źródłowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cccf7-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="cccf7-114">Jeśli nazwa pliku zawiera spację, należy ująć nazwę w cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="cccf7-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cccf7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cccf7-115">Remarks</span></span>  
 <span data-ttu-id="cccf7-116">`-doc` Opcję formantów, czy kompilator generuje plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="cccf7-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="cccf7-117">Jeśli używasz `-doc:file` składni `file` parametr określa nazwę pliku XML.</span><span class="sxs-lookup"><span data-stu-id="cccf7-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="cccf7-118">Jeśli używasz `-doc` lub `-doc+`, kompilator przyjmuje nazwę pliku XML z pliku wykonywalnego lub biblioteki, która tworzy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="cccf7-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="cccf7-119">Jeśli używasz `-doc-` lub nie określaj `-doc` opcja, kompilator nie tworzy pliku XML.</span><span class="sxs-lookup"><span data-stu-id="cccf7-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="cccf7-120">W plikach kodu źródłowego komentarzy do dokumentacji może poprzedzać następujące definicje:</span><span class="sxs-lookup"><span data-stu-id="cccf7-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="cccf7-121">Zdefiniowane przez użytkownika typów, takie jak [klasy](../../../visual-basic/language-reference/statements/class-statement.md) lub [— interfejs](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="cccf7-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="cccf7-122">Elementy członkowskie, takich jak pola, [zdarzeń](../../../visual-basic/language-reference/statements/event-statement.md), [właściwości](../../../visual-basic/language-reference/statements/property-statement.md), [funkcja](../../../visual-basic/language-reference/statements/function-statement.md), lub [podprocedury](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cccf7-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="cccf7-123">Aby utworzony plik XML za pomocą programu Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, pozostawić nazwę pliku pliku XML, jest taka sama jak zestawu mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="cccf7-123">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="cccf7-124">Upewnij się, że plik XML jest w tym samym katalogu co zestaw, dzięki czemu w przypadku zestawu odwołuje się projekt programu Visual Studio, pliku XML, który znajduje się także.</span><span class="sxs-lookup"><span data-stu-id="cccf7-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="cccf7-125">Pliki dokumentacji XML nie są wymagane przez funkcję IntelliSense dla kodu w ramach projektu lub projektów odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="cccf7-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="cccf7-126">O ile kompilacji z `/target:module`, plik XML zawierający tagi `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="cccf7-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="cccf7-127">Znaczniki Określ nazwę pliku zawierającego manifest zestawu dla pliku danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cccf7-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="cccf7-128">Zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) dotyczące metod do generowania dokumentacji komentarze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cccf7-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="cccf7-129">Można ustawić - doc w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="cccf7-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="cccf7-130">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="cccf7-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cccf7-131">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cccf7-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="cccf7-132">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="cccf7-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="cccf7-133">3.  Ustaw wartość **Generuj plik dokumentacji XML** pole.</span><span class="sxs-lookup"><span data-stu-id="cccf7-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cccf7-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="cccf7-134">Example</span></span>  
 <span data-ttu-id="cccf7-135">Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) przykładowe.</span><span class="sxs-lookup"><span data-stu-id="cccf7-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccf7-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cccf7-136">See Also</span></span>  
 [<span data-ttu-id="cccf7-137">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cccf7-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cccf7-138">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="cccf7-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)

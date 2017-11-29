---
title: /doc
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2490529b951ef6e583e3bfa54afced89c823e874
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="doc"></a><span data-ttu-id="9fd77-102">/doc</span><span class="sxs-lookup"><span data-stu-id="9fd77-102">/doc</span></span>
<span data-ttu-id="9fd77-103">Przetwarza komentarzy do dokumentacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="9fd77-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fd77-104">Syntax</span></span>  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="9fd77-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9fd77-105">Arguments</span></span>  
  
|<span data-ttu-id="9fd77-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9fd77-106">Term</span></span>|<span data-ttu-id="9fd77-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9fd77-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="9fd77-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="9fd77-108">`+` &#124; `-`</span></span>|<span data-ttu-id="9fd77-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9fd77-109">Optional.</span></span> <span data-ttu-id="9fd77-110">Określanie +, lub po prostu `/doc`, powoduje, że kompilator, aby wygenerować informacje dokumentacji i umieść go w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="9fd77-110">Specifying +, or just `/doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="9fd77-111">Określanie `-` jest odpowiednikiem nieokreślenie `/doc`, powoduje żadne informacje dokumentacji nie ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="9fd77-111">Specifying `-` is the equivalent of not specifying `/doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="9fd77-112">Jeśli wymagane `/doc:` jest używany.</span><span class="sxs-lookup"><span data-stu-id="9fd77-112">Required if `/doc:` is used.</span></span> <span data-ttu-id="9fd77-113">Określa wyjściowego pliku XML, który jest wypełniana komentarze z plików kodu źródłowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9fd77-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="9fd77-114">Jeśli nazwa pliku zawiera spację, należy ująć nazwę w cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="9fd77-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fd77-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fd77-115">Remarks</span></span>  
 <span data-ttu-id="9fd77-116">`/doc` Opcję formantów, czy kompilator generuje plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="9fd77-116">The `/doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="9fd77-117">Jeśli używasz `/doc:``file` składni `file` parametr określa nazwę pliku XML.</span><span class="sxs-lookup"><span data-stu-id="9fd77-117">If you use the `/doc:``file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="9fd77-118">Jeśli używasz `/doc` lub `/doc+`, kompilator przyjmuje nazwę pliku XML z pliku wykonywalnego lub biblioteki, która tworzy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9fd77-118">If you use `/doc` or `/doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="9fd77-119">Jeśli używasz `/doc-` lub nie określaj `/doc` opcja, kompilator nie tworzy pliku XML.</span><span class="sxs-lookup"><span data-stu-id="9fd77-119">If you use `/doc-` or do not specify the `/doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="9fd77-120">W plikach kodu źródłowego komentarzy do dokumentacji może poprzedzać następujące definicje:</span><span class="sxs-lookup"><span data-stu-id="9fd77-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="9fd77-121">Zdefiniowane przez użytkownika typów, takie jak [klasy](../../../visual-basic/language-reference/statements/class-statement.md) lub [— interfejs](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9fd77-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="9fd77-122">Elementy członkowskie, takich jak pola, [zdarzeń](../../../visual-basic/language-reference/statements/event-statement.md), [właściwości](../../../visual-basic/language-reference/statements/property-statement.md), [funkcja](../../../visual-basic/language-reference/statements/function-statement.md), lub [podprocedury](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9fd77-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="9fd77-123">Aby użyć wygenerowanego pliku XML z [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, pozostawić nazwę pliku pliku XML, jest taka sama jak zestawu mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9fd77-123">To use the generated XML file with the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="9fd77-124">Upewnij się, że plik XML jest w tym samym katalogu co zestaw, dzięki czemu podczas odwołuje się zestaw [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] projekt, plik XML znajduje się także.</span><span class="sxs-lookup"><span data-stu-id="9fd77-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] project, the .xml file is found as well.</span></span> <span data-ttu-id="9fd77-125">Pliki dokumentacji XML nie są wymagane przez funkcję IntelliSense dla kodu w ramach projektu lub projektów odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="9fd77-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="9fd77-126">O ile kompilacji z `/target:module`, plik XML zawierający tagi `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="9fd77-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="9fd77-127">Znaczniki Określ nazwę pliku zawierającego manifest zestawu dla pliku danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9fd77-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="9fd77-128">Zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) dotyczące metod do generowania dokumentacji komentarze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9fd77-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="9fd77-129">Aby ustawić/doc w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="9fd77-129">To set /doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9fd77-130">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="9fd77-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9fd77-131">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9fd77-131">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9fd77-132">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="9fd77-132">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="9fd77-133">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="9fd77-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9fd77-134">3.  Ustaw wartość **Generuj plik dokumentacji XML** pole.</span><span class="sxs-lookup"><span data-stu-id="9fd77-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9fd77-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="9fd77-135">Example</span></span>  
 <span data-ttu-id="9fd77-136">Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) przykładowe.</span><span class="sxs-lookup"><span data-stu-id="9fd77-136">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd77-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fd77-137">See Also</span></span>  
 [<span data-ttu-id="9fd77-138">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fd77-138">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9fd77-139">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="9fd77-139">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)

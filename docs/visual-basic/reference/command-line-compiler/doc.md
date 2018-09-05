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
ms.openlocfilehash: 4c77d063d64354bf4693ce82509f36be9d2e5b0c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43670967"
---
# <a name="-doc"></a><span data-ttu-id="b4b56-102">-doc</span><span class="sxs-lookup"><span data-stu-id="b4b56-102">-doc</span></span>
<span data-ttu-id="b4b56-103">Przetwarza komentarze dokumentacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="b4b56-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4b56-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4b56-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b4b56-105">Arguments</span></span>  
  
|<span data-ttu-id="b4b56-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b4b56-106">Term</span></span>|<span data-ttu-id="b4b56-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b4b56-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="b4b56-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b4b56-108">`+` &#124; `-`</span></span>|<span data-ttu-id="b4b56-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b4b56-109">Optional.</span></span> <span data-ttu-id="b4b56-110">Określanie +, lub po prostu `-doc`, powoduje, że kompilator do generowania informacji o dokumentacji i umieść go w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="b4b56-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="b4b56-111">Określanie `-` jest odpowiednikiem nie został podany `-doc`, powodując Brak informacji o dokumentacji, ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="b4b56-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="b4b56-112">Jeśli wymagane `-doc:` jest używany.</span><span class="sxs-lookup"><span data-stu-id="b4b56-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="b4b56-113">Określa wyjściowy plik XML, który jest wypełniana przy użyciu komentarzy z plików kodu źródłowego, kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b4b56-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="b4b56-114">Jeśli nazwa pliku zawiera spację, należy ująć nazwę ze znakami cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="b4b56-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4b56-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4b56-115">Remarks</span></span>  
 <span data-ttu-id="b4b56-116">`-doc` Opcji kontrolki, czy kompilator generuje plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b4b56-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="b4b56-117">Jeśli używasz `-doc:file` składni `file` parametr określa nazwę pliku XML.</span><span class="sxs-lookup"><span data-stu-id="b4b56-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="b4b56-118">Jeśli używasz `-doc` lub `-doc+`, kompilator przyjmuje nazwę pliku XML z pliku wykonywalnego lub biblioteki, która tworzy kompilator.</span><span class="sxs-lookup"><span data-stu-id="b4b56-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="b4b56-119">Jeśli używasz `-doc-` lub nie określaj `-doc` opcja, kompilator nie tworzy pliku XML.</span><span class="sxs-lookup"><span data-stu-id="b4b56-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="b4b56-120">W plikach kodu źródłowego komentarze dokumentacji może poprzedzać następujące definicje:</span><span class="sxs-lookup"><span data-stu-id="b4b56-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="b4b56-121">Zdefiniowane przez użytkownika typy, takie jak [klasy](../../../visual-basic/language-reference/statements/class-statement.md) lub [interfejsu](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b4b56-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="b4b56-122">Elementy członkowskie, takie jak pola, [zdarzeń](../../../visual-basic/language-reference/statements/event-statement.md), [właściwość](../../../visual-basic/language-reference/statements/property-statement.md), [funkcja](../../../visual-basic/language-reference/statements/function-statement.md), lub [podprocedury](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4b56-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="b4b56-123">Wygenerowany plik XML za pomocą programu Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) funkcji, niech nazwę pliku pliku XML, być taka sama jak zestawu mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b4b56-123">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="b4b56-124">Upewnij się, że plik XML jest w tym samym katalogu co zestaw, dzięki czemu w przypadku zestawu odwołuje się do projektu programu Visual Studio, pliku XML, który znajduje się także.</span><span class="sxs-lookup"><span data-stu-id="b4b56-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="b4b56-125">Pliki dokumentacji XML nie są wymagane, aby technologia IntelliSense działała dla kodu w projekcie lub w obrębie projektów odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="b4b56-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="b4b56-126">Jeśli kompilujesz z `/target:module`, plik XML zawiera tagi `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="b4b56-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="b4b56-127">Te znaczniki, określ nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b4b56-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="b4b56-128">Zobacz [tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md) sposobów generować dokumentację z komentarzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b4b56-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="b4b56-129">Aby ustawić - dokumentu w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="b4b56-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="b4b56-130">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="b4b56-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b4b56-131">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b4b56-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="b4b56-132">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="b4b56-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="b4b56-133">3.  Ustaw wartość w **soubor dokumentace XML do generowania** pole.</span><span class="sxs-lookup"><span data-stu-id="b4b56-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b4b56-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4b56-134">Example</span></span>  
 <span data-ttu-id="b4b56-135">Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) dla próbki.</span><span class="sxs-lookup"><span data-stu-id="b4b56-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b56-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4b56-136">See Also</span></span>  
 [<span data-ttu-id="b4b56-137">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4b56-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b4b56-138">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="b4b56-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)

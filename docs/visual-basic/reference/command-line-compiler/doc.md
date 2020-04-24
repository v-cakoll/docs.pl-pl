---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: a818fd46bd93682f0bede1d22b8cbc2ca6467a40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716742"
---
# <a name="-doc"></a><span data-ttu-id="c1f1f-102">-doc</span><span class="sxs-lookup"><span data-stu-id="c1f1f-102">-doc</span></span>
<span data-ttu-id="c1f1f-103">Przetwarza komentarze dokumentacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1f1f-104">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="c1f1f-105">lub</span><span class="sxs-lookup"><span data-stu-id="c1f1f-105">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1f1f-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c1f1f-106">Arguments</span></span>  
  
|<span data-ttu-id="c1f1f-107">Termin</span><span class="sxs-lookup"><span data-stu-id="c1f1f-107">Term</span></span>|<span data-ttu-id="c1f1f-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="c1f1f-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="c1f1f-109">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="c1f1f-109">`+` &#124; `-`</span></span>|<span data-ttu-id="c1f1f-110">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-110">Optional.</span></span> <span data-ttu-id="c1f1f-111">Określenie +, lub po `-doc`prostu powoduje, że kompilator generuje informacje dokumentacji i umieszcza je w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-111">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="c1f1f-112">Określenie `-` jest odpowiednikiem nieokreślenia `-doc`, co nie powoduje utworzenia informacji o dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-112">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="c1f1f-113">Wymagane, `-doc:` jeśli jest używany.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-113">Required if `-doc:` is used.</span></span> <span data-ttu-id="c1f1f-114">Określa wyjściowy plik XML, który jest wypełniany komentarzami z plików kodu źródłowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-114">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="c1f1f-115">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="c1f1f-115">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f1f-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1f1f-116">Remarks</span></span>  
 <span data-ttu-id="c1f1f-117">`-doc` Opcja określa, czy kompilator GENERUJE plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-117">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="c1f1f-118">Jeśli używasz `-doc:file` składni, `file` parametr określa nazwę pliku XML.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-118">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="c1f1f-119">Jeśli używasz `-doc` lub `-doc+`, KOMPILATOR Pobiera nazwę pliku XML z pliku wykonywalnego lub biblioteki, którą tworzy kompilator.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-119">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="c1f1f-120">Jeśli używasz `-doc-` lub nie określisz `-doc` opcji, KOMPILATOR nie tworzy pliku XML.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-120">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="c1f1f-121">W plikach kodu źródłowego Komentarze do dokumentacji mogą poprzedzać następujące definicje:</span><span class="sxs-lookup"><span data-stu-id="c1f1f-121">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="c1f1f-122">Typy zdefiniowane przez użytkownika, takie jak [Klasa](../../../visual-basic/language-reference/statements/class-statement.md) lub [interfejs](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c1f1f-122">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="c1f1f-123">Elementy członkowskie, takie jak pole, [zdarzenie](../../../visual-basic/language-reference/statements/event-statement.md), [Właściwość](../../../visual-basic/language-reference/statements/property-statement.md), [Funkcja](../../../visual-basic/language-reference/statements/function-statement.md)lub [podprocedura](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1f1f-123">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="c1f1f-124">Aby użyć wygenerowanego pliku XML z funkcją [IntelliSense](/visualstudio/ide/using-intellisense) programu Visual Studio, Zezwól, aby nazwa pliku XML była taka sama jak zestaw, który ma być obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-124">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="c1f1f-125">Upewnij się, że plik XML znajduje się w tym samym katalogu, co zestaw, aby w przypadku odwołania do zestawu w projekcie programu Visual Studio również znaleźć plik. XML.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-125">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="c1f1f-126">Pliki dokumentacji XML nie są wymagane, aby funkcja IntelliSense mogła korzystać z kodu w projekcie lub w obrębie projektów, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-126">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="c1f1f-127">Chyba że kompilujesz `-target:module`program, plik XML zawiera Tagi `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-127">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="c1f1f-128">Te znaczniki określają nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-128">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="c1f1f-129">Zobacz [Tagi komentarzy XML](../../../visual-basic/language-reference/xmldoc/index.md) , aby poznać sposoby generowania dokumentacji z komentarzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-129">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="c1f1f-130">Aby ustawić doc w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c1f1f-130">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c1f1f-131">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c1f1f-132">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-132">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c1f1f-133">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="c1f1f-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c1f1f-134">3. Ustaw wartość w polu **Generuj plik dokumentacji XML** .</span><span class="sxs-lookup"><span data-stu-id="c1f1f-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c1f1f-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1f1f-135">Example</span></span>  
 <span data-ttu-id="c1f1f-136">Zobacz [dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="c1f1f-136">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f1f-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1f1f-137">See also</span></span>

- [<span data-ttu-id="c1f1f-138">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1f1f-138">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c1f1f-139">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="c1f1f-139">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)

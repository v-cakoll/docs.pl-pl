---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 57a81983278c26090c62995f4da55c5cbfd66047
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408676"
---
# <a name="-doc"></a><span data-ttu-id="62126-102">-doc</span><span class="sxs-lookup"><span data-stu-id="62126-102">-doc</span></span>
<span data-ttu-id="62126-103">Przetwarza komentarze dokumentacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="62126-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62126-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62126-104">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="62126-105">lub</span><span class="sxs-lookup"><span data-stu-id="62126-105">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="62126-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="62126-106">Arguments</span></span>  
  
|<span data-ttu-id="62126-107">Termin</span><span class="sxs-lookup"><span data-stu-id="62126-107">Term</span></span>|<span data-ttu-id="62126-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="62126-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="62126-109">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="62126-109">`+` &#124; `-`</span></span>|<span data-ttu-id="62126-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="62126-110">Optional.</span></span> <span data-ttu-id="62126-111">Określenie +, lub po prostu `-doc` powoduje, że kompilator generuje informacje dokumentacji i umieszcza je w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="62126-111">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="62126-112">Określenie `-` jest odpowiednikiem nieokreślenia `-doc` , co nie powoduje utworzenia informacji o dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="62126-112">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="62126-113">Wymagane, jeśli `-doc:` jest używany.</span><span class="sxs-lookup"><span data-stu-id="62126-113">Required if `-doc:` is used.</span></span> <span data-ttu-id="62126-114">Określa wyjściowy plik XML, który jest wypełniany komentarzami z plików kodu źródłowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="62126-114">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="62126-115">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="62126-115">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62126-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62126-116">Remarks</span></span>  
 <span data-ttu-id="62126-117">`-doc`Opcja określa, czy kompilator generuje plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="62126-117">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="62126-118">Jeśli używasz `-doc:file` składni, `file` parametr określa nazwę pliku XML.</span><span class="sxs-lookup"><span data-stu-id="62126-118">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="62126-119">Jeśli używasz `-doc` lub `-doc+` , kompilator Pobiera nazwę pliku XML z pliku wykonywalnego lub biblioteki, którą tworzy kompilator.</span><span class="sxs-lookup"><span data-stu-id="62126-119">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="62126-120">Jeśli używasz `-doc-` lub nie określisz `-doc` opcji, kompilator nie tworzy pliku XML.</span><span class="sxs-lookup"><span data-stu-id="62126-120">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="62126-121">W plikach kodu źródłowego Komentarze do dokumentacji mogą poprzedzać następujące definicje:</span><span class="sxs-lookup"><span data-stu-id="62126-121">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="62126-122">Typy zdefiniowane przez użytkownika, takie jak [Klasa](../../language-reference/statements/class-statement.md) lub [interfejs](../../language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="62126-122">User-defined types, such as a [class](../../language-reference/statements/class-statement.md) or [interface](../../language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="62126-123">Elementy członkowskie, takie jak pole, [zdarzenie](../../language-reference/statements/event-statement.md), [Właściwość](../../language-reference/statements/property-statement.md), [Funkcja](../../language-reference/statements/function-statement.md)lub [podprocedura](../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62126-123">Members, such as a field, [event](../../language-reference/statements/event-statement.md), [property](../../language-reference/statements/property-statement.md), [function](../../language-reference/statements/function-statement.md), or [subroutine](../../language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="62126-124">Aby użyć wygenerowanego pliku XML z funkcją [IntelliSense](/visualstudio/ide/using-intellisense) programu Visual Studio, Zezwól, aby nazwa pliku XML była taka sama jak zestaw, który ma być obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="62126-124">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="62126-125">Upewnij się, że plik XML znajduje się w tym samym katalogu, co zestaw, aby w przypadku odwołania do zestawu w projekcie programu Visual Studio również znaleźć plik. XML.</span><span class="sxs-lookup"><span data-stu-id="62126-125">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="62126-126">Pliki dokumentacji XML nie są wymagane, aby funkcja IntelliSense mogła korzystać z kodu w projekcie lub w obrębie projektów, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="62126-126">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="62126-127">Chyba że kompilujesz program `-target:module` , plik XML zawiera Tagi `<assembly></assembly>` .</span><span class="sxs-lookup"><span data-stu-id="62126-127">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="62126-128">Te znaczniki określają nazwę pliku zawierającego manifest zestawu dla pliku wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="62126-128">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="62126-129">Zobacz [Tagi komentarzy XML](../../language-reference/xmldoc/index.md) , aby poznać sposoby generowania dokumentacji z komentarzy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="62126-129">See [XML Comment Tags](../../language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="62126-130">Aby ustawić doc w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="62126-130">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="62126-131">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="62126-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="62126-132">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="62126-132">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="62126-133">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="62126-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="62126-134">3. Ustaw wartość w polu **Generuj plik dokumentacji XML** .</span><span class="sxs-lookup"><span data-stu-id="62126-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="62126-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="62126-135">Example</span></span>  
 <span data-ttu-id="62126-136">Zobacz [dokumentowanie kodu za pomocą XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="62126-136">See [Documenting Your Code with XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62126-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62126-137">See also</span></span>

- [<span data-ttu-id="62126-138">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62126-138">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="62126-139">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="62126-139">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)

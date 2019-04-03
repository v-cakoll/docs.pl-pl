---
title: Dokumentowanie kodu za pomocą XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 9b53b73afb9c6b793597c00fd2eb029b18bf1f9a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831582"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="7332f-102">Dokumentowanie kodu za pomocą XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7332f-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="7332f-103">W języku Visual Basic można udokumentować kod za pomocą języka XML</span><span class="sxs-lookup"><span data-stu-id="7332f-103">In Visual Basic, you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="7332f-104">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="7332f-104">XML Documentation Comments</span></span>  
 <span data-ttu-id="7332f-105">Zapewnia prosty sposób automatycznego tworzenia dokumentacji XML dla projektów w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7332f-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="7332f-106">Automatycznie Generuj szkielet XML dla typów i elementów członkowskich i następnie podaj podsumowania, dokumentacja opisową dla każdego parametru i inne uwagi.</span><span class="sxs-lookup"><span data-stu-id="7332f-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="7332f-107">W przypadku odpowiedniej konfiguracji dokumentacji XML są automatycznie emitowane do pliku XML z taką samą nazwę jak projekt i rozszerzenie .xml.</span><span class="sxs-lookup"><span data-stu-id="7332f-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="7332f-108">Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="7332f-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="7332f-109">Plik XML można używane lub w przeciwnym razie modyfikowane jako XML.</span><span class="sxs-lookup"><span data-stu-id="7332f-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="7332f-110">Ten plik znajduje się w tym samym katalogu co plik .exe lub .dll danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="7332f-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="7332f-111">Dokumentacja XML, który rozpoczyna się od `'''`.</span><span class="sxs-lookup"><span data-stu-id="7332f-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="7332f-112">Przetwarzanie te komentarze mają pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7332f-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="7332f-113">Dokumentacja musi być poprawnie sformułowany XML.</span><span class="sxs-lookup"><span data-stu-id="7332f-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="7332f-114">Jeśli plik XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji zawiera komentarz informujący o tym, że wystąpił błąd podczas.</span><span class="sxs-lookup"><span data-stu-id="7332f-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="7332f-115">Deweloperzy są bezpłatne tworzenie własnych zestawów tagów.</span><span class="sxs-lookup"><span data-stu-id="7332f-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="7332f-116">Jest zalecany zestaw znaczników (patrz "Sekcje pokrewne" w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="7332f-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="7332f-117">Niektóre zalecane tagi mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="7332f-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="7332f-118">\<Param > tag jest używany do opisania parametrów.</span><span class="sxs-lookup"><span data-stu-id="7332f-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="7332f-119">Jeśli używane, kompilator sprawdzi, czy parametr istnieje i czy wszystkie parametry są opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="7332f-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="7332f-120">Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="7332f-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="7332f-121">`cref` Atrybutu mogą być dołączane do każdego znacznika, aby zapewnić odwołanie do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="7332f-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="7332f-122">Kompilator sprawdza, czy ten element kodu istnieje.</span><span class="sxs-lookup"><span data-stu-id="7332f-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="7332f-123">Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="7332f-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="7332f-124">Kompilator również stosuje się do dowolnej `Imports` instrukcji podczas wyszukiwania dla typu z opisem w temacie `cref` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7332f-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="7332f-125">\<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7332f-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7332f-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7332f-126">Related Sections</span></span>  
 <span data-ttu-id="7332f-127">Aby uzyskać szczegółowe informacje na temat tworzenia pliku XML z komentarzami dokumentacji zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="7332f-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7332f-128">/doc</span><span class="sxs-lookup"><span data-stu-id="7332f-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="7332f-129">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="7332f-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)  
  
-   [<span data-ttu-id="7332f-130">Przetwarzanie pliku XML</span><span class="sxs-lookup"><span data-stu-id="7332f-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="7332f-131">Instrukcje: Tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="7332f-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="7332f-132">Narzędzia XML w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7332f-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="7332f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7332f-133">See also</span></span>

- [<span data-ttu-id="7332f-134">Tworzenie aplikacji za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7332f-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="7332f-135">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7332f-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)

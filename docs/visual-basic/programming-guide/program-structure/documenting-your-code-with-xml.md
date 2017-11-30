---
title: "Dokumentowanie kodu za pomocą XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb1f366002c4f0c675c591d83aab1b31ef8f602
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="b9976-102">Dokumentowanie kodu za pomocą XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9976-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="b9976-103">W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], należy udokumentować kod za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="b9976-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="b9976-104">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="b9976-104">XML Documentation Comments</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="b9976-105">zapewnia prosty sposób automatycznego tworzenia dokumentacji XML dla projektów.</span><span class="sxs-lookup"><span data-stu-id="b9976-105"> provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="b9976-106">Można automatycznie generować szkielet XML dla typów i członków, a następnie podaj podsumowania, dokumentacja opisową dla każdego parametru i inne uwagi.</span><span class="sxs-lookup"><span data-stu-id="b9976-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="b9976-107">W przypadku odpowiedniej konfiguracji dokumentacji XML jest automatycznie wysyłanego do pliku XML z taką samą nazwę jak projektu i rozszerzenie .xml.</span><span class="sxs-lookup"><span data-stu-id="b9976-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="b9976-108">Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="b9976-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="b9976-109">Plik XML można używane lub w przeciwnym razie manipulować w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="b9976-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="b9976-110">Ten plik znajduje się w tym samym katalogu co plik .exe lub .dll danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="b9976-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="b9976-111">Plik dokumentacji XML, który rozpoczyna się od `'''`.</span><span class="sxs-lookup"><span data-stu-id="b9976-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="b9976-112">Przetwarzanie komentarze ma pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="b9976-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="b9976-113">Dokumentację musi być poprawnie sformułowanym XML.</span><span class="sxs-lookup"><span data-stu-id="b9976-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="b9976-114">Jeśli plik XML nie jest poprawnie sformułowany, generowania ostrzeżeń i pliku dokumentacji zawiera komentarz informujący o tym, że wystąpił błąd podczas.</span><span class="sxs-lookup"><span data-stu-id="b9976-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="b9976-115">Deweloperzy mogą tworzyć własne zestawu tagów.</span><span class="sxs-lookup"><span data-stu-id="b9976-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="b9976-116">Brak zalecanych zbiór znaczników (zobacz "Sekcje pokrewne" w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="b9976-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="b9976-117">Niektóre zalecane znaczniki mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="b9976-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="b9976-118">\<Param > tag jest używany do opisywania parametrów.</span><span class="sxs-lookup"><span data-stu-id="b9976-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="b9976-119">Jeśli używana, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry są opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b9976-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="b9976-120">Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b9976-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="b9976-121">`cref` Atrybut może zostać dołączony do żadnych znacznik w celu zapewnienia odwołania do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="b9976-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="b9976-122">Kompilator sprawdza, czy istnieje tego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="b9976-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="b9976-123">Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b9976-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="b9976-124">Kompilator również szanuje żadnego `Imports` instrukcje podczas wyszukiwania dla typu opisanego w `cref` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b9976-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="b9976-125">\<Podsumowania > tag jest używany przez funkcję IntelliSense w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b9976-125">The \<summary> tag is used by IntelliSense in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9976-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b9976-126">Related Sections</span></span>  
 <span data-ttu-id="b9976-127">Aby uzyskać więcej informacji na temat tworzenia pliku XML z komentarzy do dokumentacji zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="b9976-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="b9976-128">/ doc</span><span class="sxs-lookup"><span data-stu-id="b9976-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="b9976-129">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="b9976-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="b9976-130">Przetwarzanie pliku XML</span><span class="sxs-lookup"><span data-stu-id="b9976-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="b9976-131">Porady: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="b9976-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="b9976-132">Narzędzia XML w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b9976-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="b9976-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9976-133">See Also</span></span>  
 [<span data-ttu-id="b9976-134">Tworzenie aplikacji za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9976-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)  
 [<span data-ttu-id="b9976-135">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9976-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)

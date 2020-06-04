---
title: Dokumentowanie kodu za pomocą XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 324519248b90d4f61e67803a10b3cd6c566a2a04
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404865"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="1655d-102">Dokumentowanie kodu za pomocą XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1655d-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="1655d-103">W Visual Basic można udokumentować kod za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="1655d-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="1655d-104">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="1655d-104">XML Documentation Comments</span></span>

<span data-ttu-id="1655d-105">Visual Basic zapewnia łatwy sposób automatycznego tworzenia dokumentacji XML dla projektów.</span><span class="sxs-lookup"><span data-stu-id="1655d-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="1655d-106">Można automatycznie wygenerować szkielet XML dla typów i składowych, a następnie podać podsumowania, opisową dokumentację dla każdego parametru oraz inne uwagi.</span><span class="sxs-lookup"><span data-stu-id="1655d-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="1655d-107">Po wybraniu odpowiedniej konfiguracji dokumentacja XML jest automatycznie emitowana do pliku XML o takiej samej nazwie jak nazwa projektu i rozszerzenie. XML.</span><span class="sxs-lookup"><span data-stu-id="1655d-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="1655d-108">Aby uzyskać więcej informacji, zobacz [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="1655d-108">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="1655d-109">Plik XML można wykorzystać lub w inny sposób manipulować jako XML.</span><span class="sxs-lookup"><span data-stu-id="1655d-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="1655d-110">Ten plik znajduje się w tym samym katalogu, w którym znajduje się plik Output. exe lub. dll projektu.</span><span class="sxs-lookup"><span data-stu-id="1655d-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="1655d-111">Dokumentacja XML zaczyna się od `'''` .</span><span class="sxs-lookup"><span data-stu-id="1655d-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="1655d-112">Przetwarzanie tych komentarzy ma pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1655d-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="1655d-113">Dokumentacja musi być poprawnie sformułowanym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="1655d-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="1655d-114">Jeśli kod XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji zawiera komentarz informujący o wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="1655d-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="1655d-115">Deweloperzy mogą bezpłatnie tworzyć własne zestawy tagów.</span><span class="sxs-lookup"><span data-stu-id="1655d-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="1655d-116">Istnieje zalecany zestaw tagów (zobacz sekcję "sekcje pokrewne" w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="1655d-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="1655d-117">Niektóre z zalecanych tagów mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="1655d-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="1655d-118">\<param>Tag jest używany do opisywania parametrów.</span><span class="sxs-lookup"><span data-stu-id="1655d-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="1655d-119">Jeśli jest używany, kompilator sprawdzi, czy parametr istnieje i że wszystkie parametry zostały opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="1655d-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="1655d-120">Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1655d-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="1655d-121">Ten `cref` atrybut może być dołączany do dowolnego tagu w celu zapewnienia odwołania do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="1655d-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="1655d-122">Kompilator sprawdza, czy ten element kodu istnieje.</span><span class="sxs-lookup"><span data-stu-id="1655d-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="1655d-123">Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1655d-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="1655d-124">Kompilator uwzględnia również wszelkie `Imports` instrukcje podczas wyszukiwania typu opisanego w `cref` atrybucie.</span><span class="sxs-lookup"><span data-stu-id="1655d-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="1655d-125">\<summary>Tag jest używany przez funkcję IntelliSense w programie Visual Studio do wyświetlania dodatkowych informacji na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1655d-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1655d-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1655d-126">Related Sections</span></span>

<span data-ttu-id="1655d-127">Aby uzyskać szczegółowe informacje na temat tworzenia pliku XML z komentarzami dokumentacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="1655d-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="1655d-128">-doc</span><span class="sxs-lookup"><span data-stu-id="1655d-128">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="1655d-129">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="1655d-129">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="1655d-130">Przetwarzanie pliku XML</span><span class="sxs-lookup"><span data-stu-id="1655d-130">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="1655d-131">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="1655d-131">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="1655d-132">Narzędzia XML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1655d-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="1655d-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1655d-133">See also</span></span>

- [<span data-ttu-id="1655d-134">Tworzenie aplikacji za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1655d-134">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="1655d-135">Przewodnik programowania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1655d-135">Visual Basic Programming Guide</span></span>](../index.md)

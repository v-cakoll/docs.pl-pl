---
title: 'Instrukcje: Migrowanie kodu XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 2bc5cbc1b0857a82d3b0a11f05a4eb5756724546
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710846"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="a8f16-102">Instrukcje: Migrowanie kodu XslTransform</span><span class="sxs-lookup"><span data-stu-id="a8f16-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="a8f16-103">Nowe klasy XSLT zostały zaprojektowane tak, aby były bardzo podobne do istniejących klas.</span><span class="sxs-lookup"><span data-stu-id="a8f16-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="a8f16-104">Klasa <xref:System.Xml.Xsl.XslCompiledTransform> zastępuje klasę <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="a8f16-105">Arkusze stylów są kompilowane przy użyciu metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="a8f16-106">Transformacje są wykonywane przy użyciu metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="a8f16-107">W poniższych procedurach przedstawiono typowe zadania XSLT i porównano kod przy użyciu klasy <xref:System.Xml.Xsl.XslTransform> a klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="a8f16-108">Aby przekształcić plik i dane wyjściowe na identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="a8f16-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="a8f16-109">Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="a8f16-110">Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="a8f16-111">Aby skompilować arkusz stylów i użyć programu rozpoznawania nazw z poświadczeniami domyślnymi</span><span class="sxs-lookup"><span data-stu-id="a8f16-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="a8f16-112">Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="a8f16-113">Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="a8f16-114">Aby użyć parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="a8f16-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="a8f16-115">Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="a8f16-116">Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="a8f16-117">Aby włączyć obsługę skryptów XSLT</span><span class="sxs-lookup"><span data-stu-id="a8f16-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="a8f16-118">Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="a8f16-119">Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="a8f16-120">Aby załadować wyniki do obiektu DOM</span><span class="sxs-lookup"><span data-stu-id="a8f16-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="a8f16-121">Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="a8f16-122">Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a8f16-123">Klasa <xref:System.Xml.Xsl.XslCompiledTransform> nie ma metody, która zwraca wyniki transformacji XSLT jako obiekt <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="a8f16-124">Można jednak wykonać wyjście do pliku XML i załadować plik XML do innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8f16-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="a8f16-125">Aby przesłać strumieniowo wyniki do innego magazynu danych</span><span class="sxs-lookup"><span data-stu-id="a8f16-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="a8f16-126">Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="a8f16-127">Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a8f16-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f16-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8f16-128">See also</span></span>

- [<span data-ttu-id="a8f16-129">Migrowanie z klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="a8f16-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="a8f16-130">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="a8f16-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)

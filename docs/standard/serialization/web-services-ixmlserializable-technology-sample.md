---
title: "Przykładowe interfejsu IXmlSerializable technologii usług sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 72c7e9e1cbf47dd54726a16ddeb58a193d62dc31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="fe339-102">Przykładowe interfejsu IXmlSerializable technologii usług sieci Web</span><span class="sxs-lookup"><span data-stu-id="fe339-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="fe339-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="fe339-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="fe339-104">Ten przykład przedstawia sposób użycia <xref:System.Xml.Serialization.IXmlSerializable> do sterowania serializacją niestandardowych typów w usługach sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fe339-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="fe339-105">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fe339-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="fe339-106">Otwórz [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i wybierz **nowej witryny sieci Web** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="fe339-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="fe339-107">W lewym okienku **nowej witryny sieci Web** okno dialogowe, wybierz odpowiedni język programowania, a następnie w okienku po prawej stronie wybierz **usługi sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="fe339-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="fe339-108">Typ **interfejsu IXmlSerializable** jako nazwa nową usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fe339-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="fe339-109">W oknie Solution Explorer, kliknij prawym przyciskiem myszy ikonę dla Service.asmx i wybierz **usunąć**; Powtórz ten krok dla pliku plik codebehind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="fe339-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="fe339-110">Kliknij prawym przyciskiem myszy projekt w katalogu i zaznacz **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="fe339-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="fe339-111">W oknie dialogowym Przejdź do podkatalogu usługi katalogu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="fe339-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="fe339-112">Wybierz Service.asmx, a następnie powtórz ten krok dla PLiku związanym kodzie Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="fe339-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="fe339-113">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do katalogu, która zawiera katalog IXmlSerializable, który został utworzony w kroku 3 powyżej.</span><span class="sxs-lookup"><span data-stu-id="fe339-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="fe339-114">Kliknij prawym przyciskiem myszy ikonę katalogu interfejsu IXmlSerializable i wybierz **udostępnianie i zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="fe339-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="fe339-115">Na karcie Udostępnianie w sieci Web wybierz **Udostępnij ten Folder**i Potwierdź ustawienia domyślne, włącznie z nazwą interfejsu IXmlSerializable.</span><span class="sxs-lookup"><span data-stu-id="fe339-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="fe339-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="fe339-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="fe339-117">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="fe339-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="fe339-118">Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.</span><span class="sxs-lookup"><span data-stu-id="fe339-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="fe339-119">Typ **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="fe339-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe339-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe339-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>

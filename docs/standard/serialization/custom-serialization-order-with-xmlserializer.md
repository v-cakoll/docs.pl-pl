---
title: "Kolejność niestandardowej serializacji przy użyciu elementu XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e209cc0b016fe3bf0668463d9ccd3ee06784a25
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="397ef-102">Kolejność niestandardowej serializacji przy użyciu elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="397ef-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="397ef-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="397ef-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="397ef-104">W tym przykładzie pokazano, jak kontrolować kolejność elementów serializacji i zdeserializowany serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="397ef-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="397ef-105">Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.</span><span class="sxs-lookup"><span data-stu-id="397ef-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="397ef-106">Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="397ef-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="397ef-107">Otwórz okno wiersza polecenia i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="397ef-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="397ef-108">Typ **msbuild CustomOrder.sln** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="397ef-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="397ef-109">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="397ef-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="397ef-110">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="397ef-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="397ef-111">Kliknij dwukrotnie ikonę CustomOrder.sln do otwierania tego PLiku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="397ef-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="397ef-112">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="397ef-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="397ef-113">Przykładowa aplikacja korzysta z wbudowanej w podkatalogu \bin lub \bin\Debug domyślne.</span><span class="sxs-lookup"><span data-stu-id="397ef-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="397ef-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="397ef-114">See Also</span></span>  
 [<span data-ttu-id="397ef-115">Podstawowe serializacji</span><span class="sxs-lookup"><span data-stu-id="397ef-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="397ef-116">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="397ef-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="397ef-117">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="397ef-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="397ef-118">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="397ef-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="397ef-119">Serializacja</span><span class="sxs-lookup"><span data-stu-id="397ef-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="397ef-120">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="397ef-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)

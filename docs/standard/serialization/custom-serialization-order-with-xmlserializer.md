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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 16032a7df2df374d6201f8da18d563deceeeb5bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="e0c61-102">Kolejność niestandardowej serializacji przy użyciu elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="e0c61-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="e0c61-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="e0c61-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="e0c61-104">W tym przykładzie pokazano, jak kontrolować kolejność elementów serializacji i zdeserializowany serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="e0c61-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="e0c61-105">Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.</span><span class="sxs-lookup"><span data-stu-id="e0c61-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="e0c61-106">Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e0c61-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="e0c61-107">Otwórz okno wiersza polecenia i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="e0c61-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="e0c61-108">Typ **msbuild CustomOrder.sln** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e0c61-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="e0c61-109">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e0c61-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="e0c61-110">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="e0c61-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="e0c61-111">Kliknij dwukrotnie ikonę CustomOrder.sln do otwierania tego PLiku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0c61-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="e0c61-112">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="e0c61-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="e0c61-113">Przykładowa aplikacja korzysta z wbudowanej w podkatalogu \bin lub \bin\Debug domyślne.</span><span class="sxs-lookup"><span data-stu-id="e0c61-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c61-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0c61-114">See Also</span></span>  
 [<span data-ttu-id="e0c61-115">Podstawowe serializacji</span><span class="sxs-lookup"><span data-stu-id="e0c61-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="e0c61-116">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="e0c61-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="e0c61-117">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="e0c61-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="e0c61-118">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="e0c61-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="e0c61-119">Serializacja</span><span class="sxs-lookup"><span data-stu-id="e0c61-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="e0c61-120">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="e0c61-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)

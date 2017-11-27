---
title: "Porady: marki, modelu i mapowania plików zasobów osadzonych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98fb3ada369279a34ed08110644aabcbbe72a501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="49eb5-102">Porady: marki, modelu i mapowania plików zasobów osadzonych</span><span class="sxs-lookup"><span data-stu-id="49eb5-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="49eb5-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia wdrażanie modeli i mapowania plików jako zasoby osadzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49eb5-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="49eb5-104">W tej samej domenie aplikacji połączeniem jednostki musi można załadować zestawu z osadzonego modelu i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="49eb5-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="49eb5-105">Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="49eb5-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="49eb5-106">Domyślnie [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] narzędzia osadzić modelu i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="49eb5-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="49eb5-107">Podczas definiowania ręcznie modelu i mapowania plików, użyj tej procedury, aby upewnić się, że pliki są wdrażane jako zasoby osadzone razem z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49eb5-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49eb5-108">Aby zachować zasoby osadzone, należy powtórzyć całą procedurę modyfikacjach modelu i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="49eb5-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="49eb5-109">Aby osadzić modelu i mapowania plików</span><span class="sxs-lookup"><span data-stu-id="49eb5-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="49eb5-110">W **Eksploratora rozwiązań**, wybierz plik koncepcyjny (CSDL).</span><span class="sxs-lookup"><span data-stu-id="49eb5-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="49eb5-111">W **właściwości** ustawić okienku **Akcja kompilacji** do **osadzonego zasobu**.</span><span class="sxs-lookup"><span data-stu-id="49eb5-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="49eb5-112">Powtórz kroki 1 i 2 dla pliku magazynu (ssdl) i pliku mapowania (MSL).</span><span class="sxs-lookup"><span data-stu-id="49eb5-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="49eb5-113">W **Eksploratora rozwiązań**, kliknij dwukrotnie plik App.config, a następnie zmodyfikuj `Metadata` parametru w `connectionString` atrybutu na podstawie jednej z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="49eb5-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="49eb5-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="49eb5-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="49eb5-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="49eb5-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="49eb5-116">Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="49eb5-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49eb5-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="49eb5-117">Example</span></span>  
 <span data-ttu-id="49eb5-118">Następujący ciąg połączenia odwołuje się do osadzonego modelu i mapowania plików [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="49eb5-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="49eb5-119">Ten ciąg połączenia jest przechowywany w pliku App.config projektu.</span><span class="sxs-lookup"><span data-stu-id="49eb5-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="49eb5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49eb5-120">See Also</span></span>  
 [<span data-ttu-id="49eb5-121">Mapowanie i modelowania</span><span class="sxs-lookup"><span data-stu-id="49eb5-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="49eb5-122">Porady: Definiowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="49eb5-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="49eb5-123">Porady: Tworzenie ciągu połączenia EntityConnection</span><span class="sxs-lookup"><span data-stu-id="49eb5-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [<span data-ttu-id="49eb5-124">ADO.NET Entity Data Model Tools</span><span class="sxs-lookup"><span data-stu-id="49eb5-124">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)

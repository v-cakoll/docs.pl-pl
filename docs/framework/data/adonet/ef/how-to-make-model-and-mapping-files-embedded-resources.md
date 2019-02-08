---
title: 'Instrukcje: Upewnij się, modelu i mapowania plików osadzone zasoby'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 7827ecce0fe7f5c21291d3ba2edd925c6a8e5960
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826528"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="6d1b2-102">Instrukcje: Upewnij się, modelu i mapowania plików osadzone zasoby</span><span class="sxs-lookup"><span data-stu-id="6d1b2-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="6d1b2-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia wdrażanie modelu i mapowania plików jako zasoby osadzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d1b2-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="6d1b2-104">W tej samej domenie aplikacji, ponieważ połączenie jednostki musi można załadować zestawu z osadzonym modelem i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="6d1b2-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="6d1b2-105">Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="6d1b2-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="6d1b2-106">Domyślnie [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] narzędzia osadzić modelu i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="6d1b2-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="6d1b2-107">Podczas definiowania ręcznie modelu i mapowania plików, użyj tej procedury, aby upewnić się, że pliki są wdrażane jako zasoby osadzone, wraz z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d1b2-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d1b2-108">Aby zachować zasoby osadzone, należy Powtórz tę procedurę, zawsze wtedy, gdy modelu i mapowania plików są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="6d1b2-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="6d1b2-109">Aby osadzić modelu i mapowania plików</span><span class="sxs-lookup"><span data-stu-id="6d1b2-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="6d1b2-110">W **Eksploratora rozwiązań**, wybierz plik koncepcyjnej (.csdl).</span><span class="sxs-lookup"><span data-stu-id="6d1b2-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="6d1b2-111">W **właściwości** Ustaw okienku **Build Action** do **zasób osadzony**.</span><span class="sxs-lookup"><span data-stu-id="6d1b2-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="6d1b2-112">Powtórz kroki 1 i 2 dla pliku magazynu (ssdl) i pliku mapowania (MSL albo identyfikatorem).</span><span class="sxs-lookup"><span data-stu-id="6d1b2-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="6d1b2-113">W **Eksploratora rozwiązań**, kliknij dwukrotnie plik App.config, a następnie zmodyfikuj `Metadata` parametru w `connectionString` atrybutu na podstawie jednej z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="6d1b2-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="6d1b2-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="6d1b2-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="6d1b2-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="6d1b2-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="6d1b2-116">Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="6d1b2-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d1b2-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d1b2-117">Example</span></span>  
 <span data-ttu-id="6d1b2-118">Następujące parametry połączenia odwołuje się do osadzonego modelu i mapowania plików na [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="6d1b2-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="6d1b2-119">Te parametry połączenia są przechowywane w pliku App.config projektu.</span><span class="sxs-lookup"><span data-stu-id="6d1b2-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="6d1b2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d1b2-120">See also</span></span>
- [<span data-ttu-id="6d1b2-121">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="6d1b2-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [<span data-ttu-id="6d1b2-122">Instrukcje: Określanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="6d1b2-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)
- [<span data-ttu-id="6d1b2-123">Instrukcje: Tworzenie ciągu połączenia EntityConnection</span><span class="sxs-lookup"><span data-stu-id="6d1b2-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="6d1b2-124">[Narzędzia do modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6d1b2-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

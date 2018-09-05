---
title: 'Instrukcje: marka, Model i mapowanie plików zasobów osadzonych'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 35507f92d0ba9f434156773c8dc5621ed3c423c0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555353"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="05e55-102">Instrukcje: marka, Model i mapowanie plików zasobów osadzonych</span><span class="sxs-lookup"><span data-stu-id="05e55-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="05e55-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia wdrażanie modelu i mapowania plików jako zasoby osadzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05e55-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="05e55-104">W tej samej domenie aplikacji, ponieważ połączenie jednostki musi można załadować zestawu z osadzonym modelem i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="05e55-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="05e55-105">Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="05e55-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="05e55-106">Domyślnie [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] narzędzia osadzić modelu i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="05e55-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="05e55-107">Podczas definiowania ręcznie modelu i mapowania plików, użyj tej procedury, aby upewnić się, że pliki są wdrażane jako zasoby osadzone, wraz z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05e55-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05e55-108">Aby zachować zasoby osadzone, należy Powtórz tę procedurę, zawsze wtedy, gdy modelu i mapowania plików są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="05e55-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="05e55-109">Aby osadzić modelu i mapowania plików</span><span class="sxs-lookup"><span data-stu-id="05e55-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="05e55-110">W **Eksploratora rozwiązań**, wybierz plik koncepcyjnej (.csdl).</span><span class="sxs-lookup"><span data-stu-id="05e55-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="05e55-111">W **właściwości** Ustaw okienku **Build Action** do **zasób osadzony**.</span><span class="sxs-lookup"><span data-stu-id="05e55-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="05e55-112">Powtórz kroki 1 i 2 dla pliku magazynu (ssdl) i pliku mapowania (MSL albo identyfikatorem).</span><span class="sxs-lookup"><span data-stu-id="05e55-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="05e55-113">W **Eksploratora rozwiązań**, kliknij dwukrotnie plik App.config, a następnie zmodyfikuj `Metadata` parametru w `connectionString` atrybutu na podstawie jednej z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="05e55-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="05e55-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="05e55-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="05e55-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="05e55-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="05e55-116">Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="05e55-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05e55-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="05e55-117">Example</span></span>  
 <span data-ttu-id="05e55-118">Następujące parametry połączenia odwołuje się do osadzonego modelu i mapowania plików na [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="05e55-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="05e55-119">Te parametry połączenia są przechowywane w pliku App.config projektu.</span><span class="sxs-lookup"><span data-stu-id="05e55-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="05e55-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05e55-120">See Also</span></span>  
 [<span data-ttu-id="05e55-121">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="05e55-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="05e55-122">Instrukcje: Określanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="05e55-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="05e55-123">Instrukcje: Tworzenie ciągu połączenia EntityConnection</span><span class="sxs-lookup"><span data-stu-id="05e55-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [<span data-ttu-id="05e55-124">Narzędzia do modelu danych jednostki ADO.NET</span><span class="sxs-lookup"><span data-stu-id="05e55-124">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)

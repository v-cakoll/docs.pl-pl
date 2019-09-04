---
title: 'Instrukcje: Marka, model i mapowanie plików zasobów osadzonych'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: c88e0c09742d76c7508d7d782eabbe46035d3501
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251448"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="dda55-102">Instrukcje: Marka, model i mapowanie plików zasobów osadzonych</span><span class="sxs-lookup"><span data-stu-id="dda55-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="dda55-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia wdrażanie modelu i plików mapowania jako zasobów osadzonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dda55-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="dda55-104">Zestaw z osadzonym modelem i plikami mapowania musi być załadowany w tej samej domenie aplikacji co połączenie jednostki.</span><span class="sxs-lookup"><span data-stu-id="dda55-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="dda55-105">Aby uzyskać więcej informacji, zobacz [Parametry połączenia](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="dda55-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="dda55-106">Domyślnie narzędzia Entity Data Model osadzają model i pliki mapowania.</span><span class="sxs-lookup"><span data-stu-id="dda55-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="dda55-107">Podczas ręcznego definiowania modelu i plików mapowania Użyj tej procedury, aby upewnić się, że pliki są wdrażane jako zasoby osadzone razem z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacją.</span><span class="sxs-lookup"><span data-stu-id="dda55-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dda55-108">Aby zapewnić obsługę zasobów osadzonych, należy powtórzyć tę procedurę przy każdej modyfikacji modelu i plików mapowania.</span><span class="sxs-lookup"><span data-stu-id="dda55-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="dda55-109">Aby osadzić model i pliki mapowania</span><span class="sxs-lookup"><span data-stu-id="dda55-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="dda55-110">W **Eksplorator rozwiązań**wybierz plik koncepcyjny (. csdl).</span><span class="sxs-lookup"><span data-stu-id="dda55-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="dda55-111">W okienku **Właściwości** ustaw opcję **Akcja kompilacji** na **zasób osadzony**.</span><span class="sxs-lookup"><span data-stu-id="dda55-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="dda55-112">Powtórz kroki 1 i 2 dla pliku Storage (. ssdl) i pliku mapowania (. MSL).</span><span class="sxs-lookup"><span data-stu-id="dda55-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="dda55-113">W **Eksplorator rozwiązań**kliknij dwukrotnie plik App. config, a następnie zmodyfikuj `Metadata` parametr w `connectionString` atrybucie na podstawie jednego z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="dda55-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="dda55-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="dda55-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="dda55-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="dda55-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="dda55-116">Aby uzyskać więcej informacji, zobacz [Parametry połączenia](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="dda55-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dda55-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="dda55-117">Example</span></span>  
 <span data-ttu-id="dda55-118">Poniższe parametry połączenia odwołują się do osadzonego modelu i plików mapowania dla [modelu sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="dda55-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="dda55-119">Te parametry połączenia są przechowywane w pliku App. config projektu.</span><span class="sxs-lookup"><span data-stu-id="dda55-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="dda55-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dda55-120">See also</span></span>

- [<span data-ttu-id="dda55-121">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="dda55-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="dda55-122">Instrukcje: Definiowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="dda55-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="dda55-123">Instrukcje: Tworzenie parametrów połączenia usługi EntityConnection</span><span class="sxs-lookup"><span data-stu-id="dda55-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="dda55-124">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dda55-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

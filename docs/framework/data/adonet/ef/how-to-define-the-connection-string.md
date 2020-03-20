---
title: 'Instrukcje: Określanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150574"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="10047-102">Instrukcje: Określanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="10047-102">How to: Define the Connection String</span></span>

<span data-ttu-id="10047-103">W tym temacie pokazano, jak zdefiniować ciąg połączenia, który jest używany podczas łączenia się z modelem koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="10047-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="10047-104">Ten temat jest oparty na modelu koncepcyjnym [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10047-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="10047-105">Model sprzedaży AdventureWorks jest używany we wszystkich tematach związanych z zadaniami w dokumentacji entity framework.</span><span class="sxs-lookup"><span data-stu-id="10047-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="10047-106">W tym temacie przyjęto założenie, że już skonfigurowano platformę encji i zdefiniowano model sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="10047-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="10047-107">Aby uzyskać więcej informacji, zobacz [Jak: Ręczne definiowanie plików modelu i mapowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="10047-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="10047-108">Procedury opisane w tym temacie znajdują się również w temacie [Jak: Ręczne konfigurowanie projektu struktury encji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="10047-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="10047-109">Jeśli używasz Kreatora modelu danych jednostki w projekcie programu Visual Studio, automatycznie generuje plik .edmx i konfiguruje projekt do korzystania z entity framework.</span><span class="sxs-lookup"><span data-stu-id="10047-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="10047-110">Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="10047-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="10047-111">Aby zdefiniować parametry połączenia programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="10047-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="10047-112">Otwórz plik konfiguracji aplikacji projektu (app.config) i dodaj następujący parametry połączenia:</span><span class="sxs-lookup"><span data-stu-id="10047-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="10047-113">Jeśli projekt nie ma pliku konfiguracji aplikacji, można go dodać, wybierając **polecenie Dodaj nowy element** z menu **Projekt,** wybierając kategorię **Ogólne,** wybierając pozycję **Plik konfiguracji aplikacji,** a następnie klikając przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="10047-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="10047-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10047-114">See also</span></span>

- <span data-ttu-id="10047-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10047-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="10047-116">[Jak: Tworzenie nowego pliku .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10047-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="10047-117">[Narzędzia ADO.NET modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10047-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

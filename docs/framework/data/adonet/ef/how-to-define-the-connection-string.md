---
title: 'Instrukcje: Określanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 7fb722acbb13b3502d004978581701cc70118ff8
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129691"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="977f9-102">Instrukcje: Określanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="977f9-102">How to: Define the Connection String</span></span>

<span data-ttu-id="977f9-103">W tym temacie pokazano, jak zdefiniować parametry połączenia, który jest używany podczas nawiązywania połączenia z modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="977f9-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="977f9-104">Ten temat opiera się na [sprzedaży AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="977f9-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="977f9-105">W całym tematy związane z zadaniem używany jest Model sprzedaż AdventureWorks [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="977f9-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="977f9-106">W tym temacie założono, że użytkownik skonfigurował już [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i zdefiniowane AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="977f9-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="977f9-107">Aby uzyskać więcej informacji, zobacz [jak: Ręcznie zdefiniować modelu i mapowania plików](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="977f9-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="977f9-108">Procedury przedstawione w tym temacie znajdują się również w [jak: Ręczne konfigurowanie projektu programu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="977f9-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="977f9-109">Jeśli używasz [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] kreatora w projekcie programu Visual Studio automatycznie generuje plik edmx i konfiguruje projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="977f9-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="977f9-110">Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreator modelu Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="977f9-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="977f9-111">Aby zdefiniować parametry połączenia programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="977f9-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="977f9-112">Otwórz plik konfiguracji aplikacji projektu (app.config) i dodaj następujące parametry połączenia:</span><span class="sxs-lookup"><span data-stu-id="977f9-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="977f9-113">Jeśli projekt nie ma pliku konfiguracji aplikacji, możesz dodać kategorię, wybierając **Dodaj nowy element** z **projektu** menu, wybierając **ogólne** kategorii Wybieranie **pliku konfiguracji aplikacji**, a następnie klikając polecenie **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="977f9-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="977f9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="977f9-114">See also</span></span>

- <span data-ttu-id="977f9-115">[Szybki start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="977f9-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="977f9-116">[Jak: Utwórz nowy plik edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="977f9-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="977f9-117">[Narzędzia do modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="977f9-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

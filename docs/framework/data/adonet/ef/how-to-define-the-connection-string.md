---
title: 'Instrukcje: Definiowanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833952"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="c1ded-102">Instrukcje: Definiowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="c1ded-102">How to: Define the Connection String</span></span>

<span data-ttu-id="c1ded-103">W tym temacie przedstawiono sposób definiowania parametrów połączenia, które są używane podczas nawiązywania połączenia z modelem koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="c1ded-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="c1ded-104">Ten temat jest oparty na modelu koncepcyjnym [sprzedaży AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="c1ded-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="c1ded-105">Model sprzedaży AdventureWorks jest używany w całym temacie tematy związane z zadaniami w dokumentacji Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c1ded-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="c1ded-106">W tym temacie założono, że skonfigurowano już Entity Framework i zdefiniowano model sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c1ded-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c1ded-107">Aby uzyskać więcej informacji, zobacz [jak: ręcznie zdefiniować model i pliki mapowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c1ded-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="c1ded-108">Procedury opisane w tym temacie są również dołączone [do: ręczne Konfigurowanie projektu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c1ded-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="c1ded-109">W przypadku używania Kreatora Entity Data Model w projekcie programu Visual Studio program automatycznie generuje plik. edmx i konfiguruje projekt do korzystania z Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c1ded-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="c1ded-110">Aby uzyskać więcej informacji, zobacz [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c1ded-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="c1ded-111">Aby zdefiniować Entity Framework parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="c1ded-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="c1ded-112">Otwórz plik konfiguracji aplikacji projektu (App. config) i Dodaj następujące parametry połączenia:</span><span class="sxs-lookup"><span data-stu-id="c1ded-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="c1ded-113">Jeśli projekt nie ma pliku konfiguracji aplikacji, można go dodać, wybierając pozycję **Dodaj nowy element** z menu **projekt** , wybierając kategorię **Ogólne** , wybierając **plik konfiguracji aplikacji**, a następnie klikając polecenie **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="c1ded-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1ded-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1ded-114">See also</span></span>

- <span data-ttu-id="c1ded-115">[Szybki start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c1ded-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="c1ded-116">[Instrukcje: Tworzenie nowego pliku. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c1ded-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="c1ded-117">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c1ded-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

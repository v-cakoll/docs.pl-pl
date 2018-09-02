---
title: 'Używanie System.Transactions w programie ASP.NET:'
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 7b73ec970776f39a0c056e2a706d4818cda6cd72
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417623"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="4e777-102">Używanie System.Transactions w programie ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="4e777-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="4e777-103">W tym temacie opisano, jak pomyślnie użyć <xref:System.Transactions> wewnątrz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e777-103">This topic describes how you can successfully use <xref:System.Transactions> inside an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="4e777-104">Włącz DistributedTransactionPermission w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4e777-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="4e777-105"><xref:System.Transactions> obsługuje częściowo zaufanych wywołań i jest oznaczona za pomocą **AllowPartiallyTrustedCallers** atrybutu (APTCA).</span><span class="sxs-lookup"><span data-stu-id="4e777-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="4e777-106">Poziomy zaufania dla <xref:System.Transactions> są definiowane w oparciu o typy zasobów (na przykład, pamięci systemowej, zasoby udostępnione całego procesu, zasoby systemowe i inne zasoby), który <xref:System.Transactions> ujawnia i poziom zaufania, który ma być wymagany dostęp do tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="4e777-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="4e777-107">W środowisku częściowego zaufania zestawie zaufania-pełny można używać tylko transakcji w domenie aplikacji (w tym przypadku tylko zasób jest chroniony jest pamięci), chyba że udzielono <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="4e777-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="4e777-108"><xref:System.Transactions.DistributedTransactionPermission>jest wymagany przy każdym eskalacji transakcji zarządzania można zarządzać przez transakcję Koordynator MSDTC (Microsoft Distributed).</span><span class="sxs-lookup"><span data-stu-id="4e777-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="4e777-109">Tego rodzaju scenariusza wykorzystuje zasoby całego procesu i szczególnie globalne zasób, który jest zarezerwowane miejsce w dzienniku MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4e777-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="4e777-110">Przykładem użycia tego jest sieci Web frontonu z bazą danych lub aplikacji, która korzysta z bazy danych jako część usługi, które oferuje.</span><span class="sxs-lookup"><span data-stu-id="4e777-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="4e777-111">ma swój własny zestaw poziomy zaufania i kojarzy określonego zestawu uprawnień z te poziomy zaufania za pomocą zasad PLików.</span><span class="sxs-lookup"><span data-stu-id="4e777-111"> has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="4e777-112">Aby uzyskać więcej informacji, zobacz [poziomy zaufania platformy ASP.NET i pliki zasad](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span><span class="sxs-lookup"><span data-stu-id="4e777-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span></span> <span data-ttu-id="4e777-113">Zainstalowanie początkowo zestaw Windows SDK, Brak domyślnych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasad PLiki skojarzone z <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="4e777-113">When you initially install the Windows SDK, none of the default [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="4e777-114">Jako takie, gdy transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] eskalacji aplikacji, które będą zarządzane przez MSDTC, eskalacji nie powiedzie się z <xref:System.Security.SecurityException> po wymagających <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="4e777-114">As such, when your transaction in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="4e777-115">Aby włączyć eskalacji transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] środowisku częściowej relacji zaufania, należy udzielić <xref:System.Transactions.DistributedTransactionPermission> w tym samym poziomy zaufania domyślne, jak <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="4e777-115">To enable transaction escalation in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="4e777-116">Można skonfigurować własny zaufania niestandardowych zasad i plik w tym lub zmodyfikować pliki zasad domyślne, które są **Web_hightrust.config** i **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="4e777-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="4e777-117">Aby zmodyfikować pliki zasad, Dodaj **SecurityClass** elementu **DistributedTransactionPermission** do **SecurityClasses** pod  **PolicyLevel** elementu i dodać odpowiednią **interfejsu IPermission** pod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **elementu NamedPermissionSet** system.Transactions.</span><span class="sxs-lookup"><span data-stu-id="4e777-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="4e777-118">Następujący PLik konfiguracji pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="4e777-118">The following configuration file demonstrates this.</span></span>  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 <span data-ttu-id="4e777-119">Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasady zabezpieczeń, zobacz [securityPolicy — Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).</span><span class="sxs-lookup"><span data-stu-id="4e777-119">For more information about [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="4e777-120">Dynamicznej kompilacji</span><span class="sxs-lookup"><span data-stu-id="4e777-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="4e777-121">Jeśli chcesz zaimportować i używać <xref:System.Transactions> w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, która jest dynamicznie kompilowany na dostęp, należy umieścić odwołanie do <xref:System.Transactions> zestawu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4e777-121">If you want to import and use <xref:System.Transactions> in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="4e777-122">W szczególności należy dodać odwołania w obszarze **kompilacji**/**zestawy** sekcji domyślny katalog główny **Web.config** pliku konfiguracji, lub plik konfiguracji określonej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4e777-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="4e777-123">Poniższy przykład przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="4e777-123">The following example demonstrates this.</span></span>  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 <span data-ttu-id="4e777-124">Aby uzyskać więcej informacji, zobacz [Dodaj Element do zestawów dla kompilacji (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).</span><span class="sxs-lookup"><span data-stu-id="4e777-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e777-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e777-125">See Also</span></span>  
 [<span data-ttu-id="4e777-126">Poziomy zaufania platformy ASP.NET i pliki zasad</span><span class="sxs-lookup"><span data-stu-id="4e777-126">ASP.NET Trust Levels and Policy Files</span></span>](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [<span data-ttu-id="4e777-127">securityPolicy — Element (ASP.NET Settings Schema)</span><span class="sxs-lookup"><span data-stu-id="4e777-127">securityPolicy Element (ASP.NET Settings Schema)</span></span>](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [<span data-ttu-id="4e777-128">Eskalacja zarządzania transakcjami</span><span class="sxs-lookup"><span data-stu-id="4e777-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

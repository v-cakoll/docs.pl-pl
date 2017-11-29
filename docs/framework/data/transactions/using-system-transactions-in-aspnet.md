---
title: "Przy użyciu System.Transactions w programie ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a27428211fad8c5c53f2799ee832baa6c644f36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="afc73-102">Przy użyciu System.Transactions w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="afc73-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="afc73-103">W tym temacie opisano, jak pomyślnie służy <xref:System.Transactions> wewnątrz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afc73-103">This topic describes how you can successfully use <xref:System.Transactions> inside an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="afc73-104">Włącz DistributedTransactionPermission w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="afc73-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="afc73-105"><xref:System.Transactions>obsługuje częściowo zaufanych wywołań i jest oznaczony atrybutem **AllowPartiallyTrustedCallers** atrybutu (APTCA).</span><span class="sxs-lookup"><span data-stu-id="afc73-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="afc73-106">Poziomy zaufania dla <xref:System.Transactions> są zdefiniowane w oparciu o typy zasobów (na przykład pamięci systemowej, udostępnionych zasobów dla procesu, zasoby systemowe i inne zasoby), który <xref:System.Transactions> ujawnia i poziom zaufania, który ma być wymagane Aby uzyskać dostęp do tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="afc73-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="afc73-107">W środowisku częściowym zaufaniem zestawu bez pełnego zaufania można używać tylko transakcje w domenie aplikacji (w takim przypadku tylko zasób chroniony jest pamięci), chyba że ma przyznane uprawnienia <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="afc73-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="afc73-108"><xref:System.Transactions.DistributedTransactionPermission>jest wymagany przy każdym eskalacji transakcji zarządzania można zarządzać przez transakcję Koordynator MSDTC (Microsoft Distributed).</span><span class="sxs-lookup"><span data-stu-id="afc73-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="afc73-109">Tego rodzaju scenariusza wykorzystuje zasoby całego procesu i szczególnie globalne zasób, który jest zarezerwowane miejsce w dzienniku MSDTC.</span><span class="sxs-lookup"><span data-stu-id="afc73-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="afc73-110">Przykład użycia jest z bazą danych lub aplikacji, która korzysta z bazy danych w ramach usługi, które zapewnia frontonu sieci Web.</span><span class="sxs-lookup"><span data-stu-id="afc73-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="afc73-111">ma swój własny zestaw poziomy zaufania i kojarzy określonego zestawu uprawnień z te poziomy zaufania za pomocą zasad PLików.</span><span class="sxs-lookup"><span data-stu-id="afc73-111"> has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="afc73-112">[Poziomy zaufania platformy ASP.NET i pliki zasad](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span><span class="sxs-lookup"><span data-stu-id="afc73-112"> [ASP.NET Trust Levels and Policy Files](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span></span> <span data-ttu-id="afc73-113">Zainstalowanie początkowo zestaw Windows SDK, Brak domyślnych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasad PLiki skojarzone z <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="afc73-113">When you initially install the Windows SDK, none of the default [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="afc73-114">Tak, gdy transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] eskalacji aplikacji ma być zarządzany przez MSDTC, eskalacji kończy się niepowodzeniem z <xref:System.Security.SecurityException> na wymagających <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="afc73-114">As such, when your transaction in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="afc73-115">Aby włączyć eskalacji transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] środowisku częściowej relacji zaufania, należy udzielić <xref:System.Transactions.DistributedTransactionPermission> w tym samym poziomy zaufania domyślne, jak <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="afc73-115">To enable transaction escalation in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="afc73-116">Albo plik można skonfigurować własne niestandardowe zaufania poziomu i zasad do obsługi tej lub zmodyfikować zasady domyślne pliki, które są **Web_hightrust.config** i **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="afc73-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="afc73-117">Aby zmodyfikować pliki zasad, Dodaj **SecurityClass** elementu **DistributedTransactionPermission** do **SecurityClasses** elementu w obszarze  **PolicyLevel, który** element i dodaj odpowiednią **IPermission** pod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **elementu NamedPermissionSet** dla System.Transactions.</span><span class="sxs-lookup"><span data-stu-id="afc73-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="afc73-118">Następujący PLik konfiguracji pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="afc73-118">The following configuration file demonstrates this.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="afc73-119">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasady zabezpieczeń, zobacz [securityPolicy — Element (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span><span class="sxs-lookup"><span data-stu-id="afc73-119"> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] security policy, see [securityPolicy Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="afc73-120">Dynamicznej kompilacji</span><span class="sxs-lookup"><span data-stu-id="afc73-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="afc73-121">Jeśli chcesz zaimportować i używać <xref:System.Transactions> w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, która jest dynamicznie skompilowanych na dostęp, należy umieścić odwołanie do <xref:System.Transactions> zestawu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="afc73-121">If you want to import and use <xref:System.Transactions> in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="afc73-122">W szczególności należy dodać odwołanie w obszarze **kompilacji**/**zestawy** sekcji głównych domyślnego **Web.config** pliku konfiguracji lub plik konfiguracji dla określonej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="afc73-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="afc73-123">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="afc73-123">The following example demonstrates this.</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="afc73-124">[Dodaj Element do zestawów dla kompilacji (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span><span class="sxs-lookup"><span data-stu-id="afc73-124"> [add Element for assemblies for compilation (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc73-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afc73-125">See Also</span></span>  
 [<span data-ttu-id="afc73-126">Poziomy zaufania platformy ASP.NET i pliki zasad</span><span class="sxs-lookup"><span data-stu-id="afc73-126">ASP.NET Trust Levels and Policy Files</span></span>](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [<span data-ttu-id="afc73-127">securityPolicy — Element (schemat ustawień programu ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="afc73-127">securityPolicy Element (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba)  
 [<span data-ttu-id="afc73-128">Eskalacja zarządzania transakcji</span><span class="sxs-lookup"><span data-stu-id="afc73-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

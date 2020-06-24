---
title: Używanie elementu System.Transactions w programie ASP.NET
description: Użyj elementu System. Transactions w aplikacji ASP.NET. Włącz uprawnienia transakcji rozproszonych i pracuj z kompilacją dynamiczną.
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 48907faf99953e34d045a1e0d79eed8a788187b5
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141647"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="66eec-104">Używanie elementu System.Transactions w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66eec-104">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="66eec-105">W tym temacie opisano, jak można pomyślnie użyć <xref:System.Transactions> wewnątrz aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="66eec-105">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="66eec-106">Włącz DistributedTransactionPermission w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66eec-106">Enable DistributedTransactionPermission in ASP.NET</span></span>
 <span data-ttu-id="66eec-107"><xref:System.Transactions>obsługuje częściowo zaufane obiekty wywołujące i jest oznaczony `AllowPartiallyTrustedCallers` atrybutem (APTCA).</span><span class="sxs-lookup"><span data-stu-id="66eec-107"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="66eec-108">Poziomy zaufania dla programu <xref:System.Transactions> są zdefiniowane w oparciu o typy zasobów (na przykład pamięć systemowa, udostępnione zasoby dla całego procesu, zasoby systemowe i inne zasoby), które <xref:System.Transactions> udostępniają i poziom zaufania, który powinien być wymagany do uzyskiwania dostępu do tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="66eec-108">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="66eec-109">W środowisku częściowej relacji zaufania niepełnym zestawem zaufania można używać tylko transakcji w domenie aplikacji (w tym przypadku jedynym chronionym zasobem jest pamięć systemowa), chyba że zostanie on udzielony <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="66eec-109">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="66eec-110"><xref:System.Transactions.DistributedTransactionPermission>jest wymagany przy każdym eskalacji transakcji zarządzania można zarządzać przez transakcję Koordynator MSDTC (Microsoft Distributed).</span><span class="sxs-lookup"><span data-stu-id="66eec-110"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="66eec-111">Tego rodzaju scenariusza wykorzystuje zasoby całego procesu i szczególnie globalne zasób, który jest zarezerwowane miejsce w dzienniku MSDTC.</span><span class="sxs-lookup"><span data-stu-id="66eec-111">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="66eec-112">Przykładem tego użycia jest fronton sieci Web do bazy danych lub aplikacji, która korzysta z bazy danych w ramach usług, które zapewnia.</span><span class="sxs-lookup"><span data-stu-id="66eec-112">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="66eec-113">ASP.NET ma własny zestaw poziomów zaufania i kojarzy określony zestaw uprawnień z tymi poziomami zaufania za pomocą plików zasad.</span><span class="sxs-lookup"><span data-stu-id="66eec-113">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="66eec-114">Aby uzyskać więcej informacji, zobacz [ASP.NET poziomów zaufania i plików zasad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="66eec-114">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="66eec-115">Podczas pierwszej instalacji Windows SDK żaden z domyślnych plików zasad ASP.NET nie jest skojarzony z <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="66eec-115">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="66eec-116">W związku z tym, gdy transakcja w aplikacji ASP.NET jest przekazaniem do zarządzania przez MSDTC, eskalacja kończy się niepowodzeniem z <xref:System.Security.SecurityException> chwilą wymagającą <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="66eec-116">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="66eec-117">Aby włączyć eskalację transakcji w środowisku ASP.NET częściowej relacji zaufania, należy przyznać na tych <xref:System.Transactions.DistributedTransactionPermission> samych domyślnych poziomach zaufania co te <xref:System.Data.SqlClient.SqlClientPermission> .</span><span class="sxs-lookup"><span data-stu-id="66eec-117">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="66eec-118">Możesz skonfigurować własny niestandardowy poziom zaufania i plik zasad, aby go obsługiwać, lub zmodyfikować domyślne pliki zasad, które są **Web_hightrust.config** i **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="66eec-118">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="66eec-119">Aby zmodyfikować pliki zasad, Dodaj `SecurityClass` element `DistributedTransactionPermission` do `SecurityClasses` elementu w obszarze `PolicyLevel` elementu i Dodaj odpowiadający `IPermission` element w ASP.NET `NamedPermissionSet` dla System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="66eec-119">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="66eec-120">Następujący PLik konfiguracji pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="66eec-120">The following configuration file demonstrates this.</span></span>

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

 <span data-ttu-id="66eec-121">Aby uzyskać więcej informacji na temat zasad zabezpieczeń ASP.NET, zobacz [SecurityPolicy elementu (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="66eec-121">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="66eec-122">Dynamicznej kompilacji</span><span class="sxs-lookup"><span data-stu-id="66eec-122">Dynamic Compilation</span></span>
 <span data-ttu-id="66eec-123">Jeśli chcesz zaimportować i używać <xref:System.Transactions> w aplikacji ASP.NET, która jest dynamicznie kompilowana w programie Access, należy umieścić odwołanie do <xref:System.Transactions> zestawu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="66eec-123">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="66eec-124">W konkretnym przypadku należy dodać odwołanie w `compilation/assemblies` sekcji domyślnego pliku konfiguracyjnego **Web.config** głównego lub pliku konfiguracji konkretnej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="66eec-124">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="66eec-125">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="66eec-125">The following example demonstrates this.</span></span>

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

 <span data-ttu-id="66eec-126">Aby uzyskać więcej informacji, zobacz [Dodawanie elementu do zestawów dla kompilacji (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="66eec-126">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="66eec-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66eec-127">See also</span></span>

- <span data-ttu-id="66eec-128">[ASP.NET poziomów zaufania i plików zasad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="66eec-128">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="66eec-129">[securityPolicy, element (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="66eec-129">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="66eec-130">Eskalacja zarządzania transakcjami</span><span class="sxs-lookup"><span data-stu-id="66eec-130">Transaction Management Escalation</span></span>](transaction-management-escalation.md)

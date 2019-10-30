---
title: Używanie elementu System.Transactions w programie ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 2bddebc13897408839e18f42b17a9fbaefdc5b87
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040407"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="a0d32-102">Używanie elementu System.Transactions w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a0d32-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="a0d32-103">W tym temacie opisano, jak można pomyślnie użyć <xref:System.Transactions> wewnątrz aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a0d32-103">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="a0d32-104">Włącz DistributedTransactionPermission w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a0d32-104">Enable DistributedTransactionPermission in ASP.NET</span></span>
 <span data-ttu-id="a0d32-105"><xref:System.Transactions>obsługuje częściowo zaufanych wywołań i jest oznaczona za pomocą `AllowPartiallyTrustedCallers` atrybutu (APTCA).</span><span class="sxs-lookup"><span data-stu-id="a0d32-105"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="a0d32-106">Poziomy zaufania dla <xref:System.Transactions> są zdefiniowane w oparciu o typy zasobów (na przykład pamięć systemowa, udostępnione zasoby dla całego procesu, zasoby systemowe i inne zasoby), które <xref:System.Transactions> uwidaczniane i poziom zaufania, który powinien być wymagany do uzyskiwania dostępu do tych produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="a0d32-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="a0d32-107">W środowisku częściowej relacji zaufania, zestaw nie będący pełnym zaufaniem może używać tylko transakcji w domenie aplikacji (w tym przypadku jedynym chronionym zasobem jest pamięć systemowa), chyba że zostanie udzielony <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="a0d32-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="a0d32-108"><xref:System.Transactions.DistributedTransactionPermission>jest wymagany przy każdym eskalacji transakcji zarządzania można zarządzać przez transakcję Koordynator MSDTC (Microsoft Distributed).</span><span class="sxs-lookup"><span data-stu-id="a0d32-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="a0d32-109">Tego rodzaju scenariusza wykorzystuje zasoby całego procesu i szczególnie globalne zasób, który jest zarezerwowane miejsce w dzienniku MSDTC.</span><span class="sxs-lookup"><span data-stu-id="a0d32-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="a0d32-110">Przykładem tego użycia jest fronton sieci Web do bazy danych lub aplikacji, która korzysta z bazy danych w ramach usług, które zapewnia.</span><span class="sxs-lookup"><span data-stu-id="a0d32-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="a0d32-111">ASP.NET ma własny zestaw poziomów zaufania i kojarzy określony zestaw uprawnień z tymi poziomami zaufania za pomocą plików zasad.</span><span class="sxs-lookup"><span data-stu-id="a0d32-111">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="a0d32-112">Aby uzyskać więcej informacji, zobacz [ASP.NET poziomów zaufania i plików zasad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a0d32-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="a0d32-113">Podczas pierwszej instalacji Windows SDK żadne z domyślnych plików zasad ASP.NET nie są skojarzone z <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="a0d32-113">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="a0d32-114">W związku z tym, gdy transakcja w aplikacji ASP.NET jest przekazaniem do zarządzania przez MSDTC, eskalacja kończy się niepowodzeniem z <xref:System.Security.SecurityException> na <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="a0d32-114">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="a0d32-115">Aby włączyć eskalację transakcji w środowisku ASP.NET częściowego zaufania, należy przyznać <xref:System.Transactions.DistributedTransactionPermission> na tych samych domyślnych poziomach zaufania co w przypadku <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="a0d32-115">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="a0d32-116">Możesz skonfigurować własny niestandardowy poziom zaufania i plik zasad, aby go obsługiwać, lub zmodyfikować domyślne pliki zasad, które są **Web_hightrust. config** i **web_mediumtrust. config**.</span><span class="sxs-lookup"><span data-stu-id="a0d32-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="a0d32-117">Aby zmodyfikować pliki zasad, Dodaj element `SecurityClass` dla `DistributedTransactionPermission` do elementu `SecurityClasses` w obszarze `PolicyLevel` i Dodaj odpowiedni element `IPermission` w obszarze ASP.NET `NamedPermissionSet` dla elementu System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="a0d32-117">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="a0d32-118">Następujący PLik konfiguracji pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="a0d32-118">The following configuration file demonstrates this.</span></span>

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

 <span data-ttu-id="a0d32-119">Aby uzyskać więcej informacji na temat zasad zabezpieczeń ASP.NET, zobacz [SecurityPolicy elementu (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a0d32-119">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="a0d32-120">Dynamicznej kompilacji</span><span class="sxs-lookup"><span data-stu-id="a0d32-120">Dynamic Compilation</span></span>
 <span data-ttu-id="a0d32-121">Jeśli chcesz zaimportować i używać <xref:System.Transactions> w aplikacji ASP.NET, która jest dynamicznie kompilowana w programie Access, należy umieścić odwołanie do zestawu <xref:System.Transactions> w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a0d32-121">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="a0d32-122">W konkretnym przypadku należy dodać odwołanie do sekcji `compilation/assemblies` domyślnego głównego pliku konfiguracyjnego **Web. config** lub pliku konfiguracji konkretnej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a0d32-122">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="a0d32-123">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="a0d32-123">The following example demonstrates this.</span></span>

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

 <span data-ttu-id="a0d32-124">Aby uzyskać więcej informacji, zobacz [Dodawanie elementu do zestawów dla kompilacji (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a0d32-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0d32-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0d32-125">See also</span></span>

- <span data-ttu-id="a0d32-126">[ASP.NET poziomów zaufania i plików zasad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0d32-126">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="a0d32-127">[securityPolicy, element (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0d32-127">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="a0d32-128">Eskalacja zarządzania transakcjami</span><span class="sxs-lookup"><span data-stu-id="a0d32-128">Transaction Management Escalation</span></span>](transaction-management-escalation.md)

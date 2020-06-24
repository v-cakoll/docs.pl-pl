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
# <a name="using-systemtransactions-in-aspnet"></a>Używanie elementu System.Transactions w programie ASP.NET
W tym temacie opisano, jak można pomyślnie użyć <xref:System.Transactions> wewnątrz aplikacji ASP.NET.

## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Włącz DistributedTransactionPermission w programie ASP.NET
 <xref:System.Transactions>obsługuje częściowo zaufane obiekty wywołujące i jest oznaczony `AllowPartiallyTrustedCallers` atrybutem (APTCA). Poziomy zaufania dla programu <xref:System.Transactions> są zdefiniowane w oparciu o typy zasobów (na przykład pamięć systemowa, udostępnione zasoby dla całego procesu, zasoby systemowe i inne zasoby), które <xref:System.Transactions> udostępniają i poziom zaufania, który powinien być wymagany do uzyskiwania dostępu do tych zasobów. W środowisku częściowej relacji zaufania niepełnym zestawem zaufania można używać tylko transakcji w domenie aplikacji (w tym przypadku jedynym chronionym zasobem jest pamięć systemowa), chyba że zostanie on udzielony <xref:System.Transactions.DistributedTransactionPermission> .

 <xref:System.Transactions.DistributedTransactionPermission>jest wymagany przy każdym eskalacji transakcji zarządzania można zarządzać przez transakcję Koordynator MSDTC (Microsoft Distributed). Tego rodzaju scenariusza wykorzystuje zasoby całego procesu i szczególnie globalne zasób, który jest zarezerwowane miejsce w dzienniku MSDTC. Przykładem tego użycia jest fronton sieci Web do bazy danych lub aplikacji, która korzysta z bazy danych w ramach usług, które zapewnia.

 ASP.NET ma własny zestaw poziomów zaufania i kojarzy określony zestaw uprawnień z tymi poziomami zaufania za pomocą plików zasad. Aby uzyskać więcej informacji, zobacz [ASP.NET poziomów zaufania i plików zasad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Podczas pierwszej instalacji Windows SDK żaden z domyślnych plików zasad ASP.NET nie jest skojarzony z <xref:System.Transactions.DistributedTransactionPermission> . W związku z tym, gdy transakcja w aplikacji ASP.NET jest przekazaniem do zarządzania przez MSDTC, eskalacja kończy się niepowodzeniem z <xref:System.Security.SecurityException> chwilą wymagającą <xref:System.Transactions.DistributedTransactionPermission> . Aby włączyć eskalację transakcji w środowisku ASP.NET częściowej relacji zaufania, należy przyznać na tych <xref:System.Transactions.DistributedTransactionPermission> samych domyślnych poziomach zaufania co te <xref:System.Data.SqlClient.SqlClientPermission> . Możesz skonfigurować własny niestandardowy poziom zaufania i plik zasad, aby go obsługiwać, lub zmodyfikować domyślne pliki zasad, które są **Web_hightrust.config** i **Web_mediumtrust.config**.

 Aby zmodyfikować pliki zasad, Dodaj `SecurityClass` element `DistributedTransactionPermission` do `SecurityClasses` elementu w obszarze `PolicyLevel` elementu i Dodaj odpowiadający `IPermission` element w ASP.NET `NamedPermissionSet` dla System. Transactions. Następujący PLik konfiguracji pokazuje to.

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

 Aby uzyskać więcej informacji na temat zasad zabezpieczeń ASP.NET, zobacz [SecurityPolicy elementu (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).

## <a name="dynamic-compilation"></a>Dynamicznej kompilacji
 Jeśli chcesz zaimportować i używać <xref:System.Transactions> w aplikacji ASP.NET, która jest dynamicznie kompilowana w programie Access, należy umieścić odwołanie do <xref:System.Transactions> zestawu w pliku konfiguracji. W konkretnym przypadku należy dodać odwołanie w `compilation/assemblies` sekcji domyślnego pliku konfiguracyjnego **Web.config** głównego lub pliku konfiguracji konkretnej aplikacji sieci Web. Poniższy przykład ilustruje to.

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

 Aby uzyskać więcej informacji, zobacz [Dodawanie elementu do zestawów dla kompilacji (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).

## <a name="see-also"></a>Zobacz też

- [ASP.NET poziomów zaufania i plików zasad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy, element (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Eskalacja zarządzania transakcjami](transaction-management-escalation.md)

---
title: Przy użyciu System.Transactions w programie ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 142f5e18682b02dfb659959a19b79c10fb3110c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-systemtransactions-in-aspnet"></a>Przy użyciu System.Transactions w programie ASP.NET
W tym temacie opisano, jak pomyślnie służy <xref:System.Transactions> wewnątrz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Włącz DistributedTransactionPermission w programie ASP.NET  
 <xref:System.Transactions> obsługuje częściowo zaufanych wywołań i jest oznaczony atrybutem **AllowPartiallyTrustedCallers** atrybutu (APTCA). Poziomy zaufania dla <xref:System.Transactions> są zdefiniowane w oparciu o typy zasobów (na przykład pamięci systemowej, udostępnionych zasobów dla procesu, zasoby systemowe i inne zasoby), który <xref:System.Transactions> ujawnia i poziom zaufania, który ma być wymagane Aby uzyskać dostęp do tych zasobów. W środowisku częściowym zaufaniem zestawu bez pełnego zaufania można używać tylko transakcje w domenie aplikacji (w takim przypadku tylko zasób chroniony jest pamięci), chyba że ma przyznane uprawnienia <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission>jest wymagany przy każdym eskalacji transakcji zarządzania można zarządzać przez transakcję Koordynator MSDTC (Microsoft Distributed). Tego rodzaju scenariusza wykorzystuje zasoby całego procesu i szczególnie globalne zasób, który jest zarezerwowane miejsce w dzienniku MSDTC. Przykład użycia jest z bazą danych lub aplikacji, która korzysta z bazy danych w ramach usługi, które zapewnia frontonu sieci Web.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]ma swój własny zestaw poziomy zaufania i kojarzy określonego zestawu uprawnień z te poziomy zaufania za pomocą zasad PLików. Aby uzyskać więcej informacji, zobacz [poziomy zaufania platformy ASP.NET i pliki zasad](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1). Zainstalowanie początkowo zestaw Windows SDK, Brak domyślnych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasad PLiki skojarzone z <xref:System.Transactions.DistributedTransactionPermission>. Tak, gdy transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] eskalacji aplikacji ma być zarządzany przez MSDTC, eskalacji kończy się niepowodzeniem z <xref:System.Security.SecurityException> na wymagających <xref:System.Transactions.DistributedTransactionPermission>. Aby włączyć eskalacji transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] środowisku częściowej relacji zaufania, należy udzielić <xref:System.Transactions.DistributedTransactionPermission> w tym samym poziomy zaufania domyślne, jak <xref:System.Data.SqlClient.SqlClientPermission>. Albo plik można skonfigurować własne niestandardowe zaufania poziomu i zasad do obsługi tej lub zmodyfikować zasady domyślne pliki, które są **Web_hightrust.config** i **Web_mediumtrust.config**.  
  
 Aby zmodyfikować pliki zasad, Dodaj **SecurityClass** elementu **DistributedTransactionPermission** do **SecurityClasses** elementu w obszarze  **PolicyLevel, który** element i dodaj odpowiednią **IPermission** pod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **elementu NamedPermissionSet** dla System.Transactions. Następujący PLik konfiguracji pokazuje to.  
  
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
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasady zabezpieczeń, zobacz [securityPolicy — Element (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).  
  
## <a name="dynamic-compilation"></a>Dynamicznej kompilacji  
 Jeśli chcesz zaimportować i używać <xref:System.Transactions> w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, która jest dynamicznie skompilowanych na dostęp, należy umieścić odwołanie do <xref:System.Transactions> zestawu w pliku konfiguracji. W szczególności należy dodać odwołanie w obszarze **kompilacji**/**zestawy** sekcji głównych domyślnego **Web.config** pliku konfiguracji lub plik konfiguracji dla określonej aplikacji sieci Web. W poniższym przykładzie pokazano to.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Dodaj Element do zestawów dla kompilacji (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).  
  
## <a name="see-also"></a>Zobacz też  
 [Poziomy zaufania platformy ASP.NET i pliki zasad](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [securityPolicy — Element (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [Eskalacja zarządzania transakcjami](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

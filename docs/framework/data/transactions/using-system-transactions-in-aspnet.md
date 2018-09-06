---
title: 'Używanie System.Transactions w programie ASP.NET:'
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 7b73ec970776f39a0c056e2a706d4818cda6cd72
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036218"
---
# <a name="using-systemtransactions-in-aspnet"></a>Używanie System.Transactions w programie ASP.NET:
W tym temacie opisano, jak pomyślnie użyć <xref:System.Transactions> wewnątrz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Włącz DistributedTransactionPermission w programie ASP.NET  
 <xref:System.Transactions> obsługuje częściowo zaufanych wywołań i jest oznaczona za pomocą **AllowPartiallyTrustedCallers** atrybutu (APTCA). Poziomy zaufania dla <xref:System.Transactions> są definiowane w oparciu o typy zasobów (na przykład, pamięci systemowej, zasoby udostępnione całego procesu, zasoby systemowe i inne zasoby), który <xref:System.Transactions> ujawnia i poziom zaufania, który ma być wymagany dostęp do tych zasobów. W środowisku częściowego zaufania zestawie zaufania-pełny można używać tylko transakcji w domenie aplikacji (w tym przypadku tylko zasób jest chroniony jest pamięci), chyba że udzielono <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission>jest wymagany przy każdym eskalacji transakcji zarządzania można zarządzać przez transakcję Koordynator MSDTC (Microsoft Distributed). Tego rodzaju scenariusza wykorzystuje zasoby całego procesu i szczególnie globalne zasób, który jest zarezerwowane miejsce w dzienniku MSDTC. Przykładem użycia tego jest sieci Web frontonu z bazą danych lub aplikacji, która korzysta z bazy danych jako część usługi, które oferuje.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]ma swój własny zestaw poziomy zaufania i kojarzy określonego zestawu uprawnień z te poziomy zaufania za pomocą zasad PLików. Aby uzyskać więcej informacji, zobacz [poziomy zaufania platformy ASP.NET i pliki zasad](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1). Zainstalowanie początkowo zestaw Windows SDK, Brak domyślnych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasad PLiki skojarzone z <xref:System.Transactions.DistributedTransactionPermission>. Jako takie, gdy transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] eskalacji aplikacji, które będą zarządzane przez MSDTC, eskalacji nie powiedzie się z <xref:System.Security.SecurityException> po wymagających <xref:System.Transactions.DistributedTransactionPermission>. Aby włączyć eskalacji transakcji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] środowisku częściowej relacji zaufania, należy udzielić <xref:System.Transactions.DistributedTransactionPermission> w tym samym poziomy zaufania domyślne, jak <xref:System.Data.SqlClient.SqlClientPermission>. Można skonfigurować własny zaufania niestandardowych zasad i plik w tym lub zmodyfikować pliki zasad domyślne, które są **Web_hightrust.config** i **Web_mediumtrust.config**.  
  
 Aby zmodyfikować pliki zasad, Dodaj **SecurityClass** elementu **DistributedTransactionPermission** do **SecurityClasses** pod  **PolicyLevel** elementu i dodać odpowiednią **interfejsu IPermission** pod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **elementu NamedPermissionSet** system.Transactions. Następujący PLik konfiguracji pokazuje to.  
  
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
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zasady zabezpieczeń, zobacz [securityPolicy — Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).  
  
## <a name="dynamic-compilation"></a>Dynamicznej kompilacji  
 Jeśli chcesz zaimportować i używać <xref:System.Transactions> w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, która jest dynamicznie kompilowany na dostęp, należy umieścić odwołanie do <xref:System.Transactions> zestawu w pliku konfiguracji. W szczególności należy dodać odwołania w obszarze **kompilacji**/**zestawy** sekcji domyślny katalog główny **Web.config** pliku konfiguracji, lub plik konfiguracji określonej aplikacji sieci Web. Poniższy przykład przedstawia to.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Dodaj Element do zestawów dla kompilacji (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).  
  
## <a name="see-also"></a>Zobacz też  
 [Poziomy zaufania platformy ASP.NET i pliki zasad](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [securityPolicy — Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [Eskalacja zarządzania transakcjami](../../../../docs/framework/data/transactions/transaction-management-escalation.md)

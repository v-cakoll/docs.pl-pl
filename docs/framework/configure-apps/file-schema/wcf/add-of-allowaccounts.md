---
title: <add> dla <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1ed0b5025ab969c45d7440f2a209426c5c87f549
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920289"
---
# <a name="add-of-allowaccounts"></a>\<Dodawanie > \<allowAccounts >
Określa konto użytkownika dla procesów, które obsługują usługi WCF i ma dostęp do połączenia z usługą udostępniania.  
  
 \<system.serviceModel.activation>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|securityIdentifier|Ciąg określający unikatowy identyfikator używany do identyfikowania konta użytkownika. Wartości domyślne to LocalSystem, Administratorzy, NS, LS i IIS_USRS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybut służący do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguracji dodaje pięć domyślnych identyfikatorów kont użytkowników do tej kolekcji.  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>

---
title: Zmienianie nazwy usługi WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8cb86621972423f55bfa18c60c1d4eb60cacb205
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651039"
---
# <a name="renaming-a-wcf-service"></a>Zmienianie nazwy usługi WCF
W tym temacie opisano, jak można zmienić nazwy usługi Windows Communication Foundation (WCF).  
  
## <a name="renaming-a-wcf-service"></a>Zmienianie nazwy usługi WCF  
 Wykonaj poniższe kroki, aby zmienić nazwy usługi w szablonie usługi Windows Communication Foundation (WCF)  
  
- Zmień nazwę klasy, która implementuje usługę.  
  
- W pliku konfiguracji usługi należy zmienić nazwy usługi na nową nazwę, które zostały wybrane, jak wskazano w poniższym przykładzie. Plik konfiguracji może być plik app.config lub web.config, w zależności od modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- Jeśli usługa jest webhosted, używa pliku *.svc. Otwórz plik svc i zmodyfikuj nazwę usługi, jak wskazano w poniższym przykładzie. Ten krok nie jest niezbędne do samodzielnie hostowanej aplikacji, ponieważ plik svc nie istnieje.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Zmiana nazwy kontraktu usługi WCF  
  
- Wykonaj następujące kroki, aby zmienić nazwę kontraktu usługi  
  
- Zmień nazwę kontraktu usługi.  
  
- W pliku konfiguracji usługi należy zmienić nazwy kontraktu usługi na nową nazwę, które zostały wybrane, jak wskazano w poniższym przykładzie. Plik konfiguracji może być plik app.config lub web.config, w zależności od modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```

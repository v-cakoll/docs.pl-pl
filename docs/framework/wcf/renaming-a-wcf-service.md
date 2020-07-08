---
title: Zmienianie nazwy usługi WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052055"
---
# <a name="renaming-a-wcf-service"></a>Zmienianie nazwy usługi WCF
W tym temacie opisano, jak można zmienić nazwę usługi Windows Communication Foundation (WCF).  
  
## <a name="renaming-a-wcf-service"></a>Zmienianie nazwy usługi WCF  
 Aby zmienić nazwę usługi w szablonie Windows Communication Foundation (WCF), wykonaj następujące czynności:  
  
- Zmień nazwę klasy implementującej usługę.  
  
- W pliku konfiguracji usługi Zmień nazwę usługi na nową wybraną nazwę, jak pokazano w poniższym przykładzie. Plik konfiguracji może być app.config lub web.config pliku w zależności od modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- Jeśli usługa jest hostowana w sieci, używa pliku * \* SVC* . Otwórz plik SVC i zmodyfikuj nazwę usługi, jak pokazano w poniższym przykładzie. Ten krok nie jest konieczny w przypadku aplikacji samodzielnych, ponieważ nie ma pliku SVC.  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Zmiana nazwy kontraktu usługi WCF  
  
- Aby zmienić nazwę kontraktu usługi, wykonaj następujące kroki:  
  
- Zmień nazwę kontraktu usługi.  
  
- W pliku konfiguracji usługi Zmień nazwę kontraktu usługi na nową wybraną nazwę, jak pokazano w poniższym przykładzie. Plik konfiguracji może być app.config lub web.config pliku w zależności od modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```

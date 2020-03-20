---
title: Zabezpieczenia komunikatów — Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 8706eee341dd1a5852efae0aad5195e09f62fec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183491"
---
# <a name="message-security-windows"></a>Zabezpieczenia komunikatów — Windows
W tym przykładzie pokazano, <xref:System.ServiceModel.WSHttpBinding> jak skonfigurować powiązanie do używania zabezpieczeń na poziomie wiadomości z uwierzytelnianiem systemu Windows. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym przykładzie usługa jest hostowana w internetowych usługach informacyjnych (IIS), a klient jest aplikacją konsoli (.exe).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Domyślnym [ \<zabezpieczeniem>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) jest zabezpieczenie wiadomości przy użyciu uwierzytelniania systemu Windows. Pliki konfiguracyjne w tym `mode` przykładzie jawnie ustawiają `Message` atrybut `clientCredentialType` [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) zabezpieczeń `Windows`i atrybut do . Te wartości są wartościami domyślnymi dla tego powiązania, ale zostały jawnie skonfigurowane, jak pokazano w poniższej konfiguracji przykładowej, aby zademonstrować ich użycie.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i umowy. Powiązanie klienta jest skonfigurowane `securityMode` `authenticationMode`z odpowiednimi i .  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"
            binding="wsHttpBinding"
            bindingConfiguration="Binding1"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Kod źródłowy usługi został zmodyfikowany, <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> aby zademonstrować, jak można uzyskać dostęp do tożsamości obiektu wywołującego.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Pierwsza metoda o `GetCallerIdentity` nazwie - - zwraca nazwę tożsamości wywołującego z powrotem do klienta. Naciśnij klawisz ENTER w oknie konsoli, aby wyłączyć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  

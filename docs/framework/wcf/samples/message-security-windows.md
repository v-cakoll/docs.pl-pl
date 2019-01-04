---
title: Zabezpieczenia komunikatów — Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: e5bb27980f38237f69f77721578f30df3830ade2
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029648"
---
# <a name="message-security-windows"></a>Zabezpieczenia komunikatów — Windows
W tym przykładzie przedstawiono sposób konfigurowania <xref:System.ServiceModel.WSHttpBinding> powiązania do użycia zabezpieczenia na poziomie komunikatu z uwierzytelnianiem Windows. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym przykładzie usługa jest hostowana w Internet Information Services (IIS), a klient to aplikacja konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Domyślne zabezpieczenia dla [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) jest zabezpieczenie wiadomości przy użyciu uwierzytelniania Windows. Pliki konfiguracji, w tym przykładzie jawnie ustawić `mode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) do `Message` i `clientCredentialType` atrybutu `Windows`. Te wartości są wartości domyślne dla tego powiązania, ale zostały jawnie skonfigurowane, jak pokazano w poniższym Przykładowa konfiguracja do zademonstrowania ich użycie.  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z adresem bezwzględnym dla punktu końcowego usługi, powiązanie i zamówienia. Klient powiązanie skonfigurowano odpowiednie `securityMode` i `authenticationMode`.  
  
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
  
 Kod źródłowy usługi została zmodyfikowana, aby zademonstrować sposób, w jaki <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> mogą być używane do dostępu tożsamość obiektu wywołującego.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Pierwsza metoda wywoływana - `GetCallerIdentity` — zwraca nazwę tożsamość obiektu wywołującego do klienta. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też

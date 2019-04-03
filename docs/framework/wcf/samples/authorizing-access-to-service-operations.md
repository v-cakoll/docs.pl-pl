---
title: Autoryzowanie dostępu do operacji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 50b6ab528aaebabbe709104632e269dfa68072a5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842372"
---
# <a name="authorizing-access-to-service-operations"></a>Autoryzowanie dostępu do operacji usługi
W tym przykładzie przedstawiono sposób użycia [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu do autoryzowania dostępu do operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) próbki. Usługi i klienta są konfigurowane za pomocą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) został ustawiony na `Message` i `clientCredentialType` został ustawiony na `Windows`. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowane do każdej metody usługi i używany do ograniczania dostępu do każdej operacji. Obiekt wywołujący musi być Windows administratorowi dostęp do każdej operacji.  
  
 W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Korzysta z pliku konfiguracji usługi [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) można ustawić `principalPermissionMode` atrybutu:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Ustawienie `principalPermissionMode` do `UseWindowsGroups` umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> na podstawie nazw grupy Windows.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowany do każdej operacji, aby wymagać obiekt wywołujący, aby być częścią grupy administratorów Windows, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie komunikuje się z każdej operacji, jeśli jest uruchomiony przy użyciu konta należącego do grupy Administratorzy; w przeciwnym razie odmowa dostępu. Aby eksperymentować z błąd autoryzacji, uruchom klienta przy użyciu konta, które nie jest częścią grupy administratorów. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.  
  
 Usługa może zostać poinformowany o błędy autoryzacji przez zaimplementowanie <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Zobacz [rozszerzanie kontroli nad obsługę błędów i raportowanie](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informacji o implementowaniu `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  

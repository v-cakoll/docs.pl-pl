---
title: Autoryzowanie dostępu do operacji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: a0ea82c876b3bd8c2a3218f84399fbb69e1d0080
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932498"
---
# <a name="authorizing-access-to-service-operations"></a>Autoryzowanie dostępu do operacji usługi
Ten przykład pokazuje, <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) jak używać > ServiceAuthorization, aby umożliwić korzystanie z atrybutu w celu autoryzacji dostępu do operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) przykładzie. Usługa i klient są konfigurowane przy użyciu [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `Message` `clientCredentialType`Atrybut> zabezpieczeń został ustawiony na wartość i został ustawiony na `Windows`. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `mode` <xref:System.Security.Permissions.PrincipalPermissionAttribute> Stosuje się do każdej metody usługi i służy do ograniczania dostępu do każdej operacji. Obiekt wywołujący musi być administratorem systemu Windows, aby uzyskać dostęp do każdej operacji.  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi używa [ \<> ServiceAuthorization](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) , aby ustawić `principalPermissionMode` atrybut:  
  
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
  
 `principalPermissionMode` Ustawienie do `UseWindowsGroups` umożliwia Korzystanie<xref:System.Security.Permissions.PrincipalPermissionAttribute> z nazw grup systemu Windows.  
  
 Program <xref:System.Security.Permissions.PrincipalPermissionAttribute> jest stosowany do każdej operacji, aby wymagać, aby wywołujący należał do grupy administratorów systemu Windows, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie komunikuje się z każdą operacją, jeśli jest uruchomiona przy użyciu konta należącego do grupy Administratorzy; w przeciwnym razie odmowa dostępu. Aby eksperymentować z błędem autoryzacji, uruchom klienta w ramach konta, które nie jest częścią grupy Administratorzy. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta programu.  
  
 Usługa może być powiadamiana o błędach autoryzacji przez implementację <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Zobacz [Rozszerzanie kontroli nad obsługą błędów i raportowanie](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informacji o `IErrorHandler`wdrażaniu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  

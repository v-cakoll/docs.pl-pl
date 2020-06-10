---
title: Autoryzowanie dostępu do operacji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 3097c86f50a75dec8a649ca4e1edd2511a046ca8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585535"
---
# <a name="authorizing-access-to-service-operations"></a>Autoryzowanie dostępu do operacji usługi
W tym przykładzie pokazano, jak użyć, [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) Aby umożliwić użycie <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu w celu autoryzacji dostępu do operacji usługi. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) przykładzie. Usługa i klient są konfigurowane przy użyciu [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . `mode`Atrybut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) został ustawiony na `Message` i `clientCredentialType` został ustawiony na `Windows` . <xref:System.Security.Permissions.PrincipalPermissionAttribute>Stosuje się do każdej metody usługi i służy do ograniczania dostępu do każdej operacji. Obiekt wywołujący musi być administratorem systemu Windows, aby uzyskać dostęp do każdej operacji.  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi używa [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) do ustawienia `principalPermissionMode` atrybutu:  
  
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
  
 Ustawienie `principalPermissionMode` do `UseWindowsGroups` umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> nazw grup systemu Windows.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>Program jest stosowany do każdej operacji, aby wymagać, aby wywołujący należał do grupy administratorów systemu Windows, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Usługa może być powiadamiana o błędach autoryzacji przez implementację <xref:System.ServiceModel.Dispatcher.IErrorHandler> . Zobacz [Rozszerzanie kontroli nad obsługą błędów i raportowanie](extending-control-over-error-handling-and-reporting.md) informacji o wdrażaniu `IErrorHandler` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  

---
title: Autoryzowanie dostępu do operacji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183923"
---
# <a name="authorizing-access-to-service-operations"></a>Autoryzowanie dostępu do operacji usługi
W tym przykładzie pokazano, jak używać [ \<serviceAuthorization>,](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) aby włączyć korzystanie z atrybutu <xref:System.Security.Permissions.PrincipalPermissionAttribute> do autoryzowania dostępu do operacji serwisowych. Ten przykład jest oparty na próbce [Wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Usługa i klient są konfigurowane przy użyciu [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Atrybut `mode` [ \<>zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) został ustawiony `Message` na . `clientCredentialType` `Windows` Jest <xref:System.Security.Permissions.PrincipalPermissionAttribute> stosowany do każdej metody usługi i służy do ograniczania dostępu do każdej operacji. Wywołujący musi być administratorem systemu Windows, aby uzyskać dostęp do każdej operacji.  
  
 W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi używa [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do `principalPermissionMode` ustawienia atrybutu:  
  
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
  
 `principalPermissionMode` Ustawienie, `UseWindowsGroups` aby włączyć <xref:System.Security.Permissions.PrincipalPermissionAttribute> korzystanie z oparte na nazwach grup systemu Windows.  
  
 Jest <xref:System.Security.Permissions.PrincipalPermissionAttribute> stosowany do każdej operacji, aby wymagać, aby wywołujący być częścią grupy administratorów systemu Windows, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie komunikuje się z każdą operacją, jeśli działa na koncie należącym do grupy Administratorzy; w przeciwnym razie odmowa dostępu. Aby eksperymentować z niepowodzeniem autoryzacji, uruchom klienta na koncie, które nie jest częścią grupy Administratorzy. Naciśnij klawisz ENTER w oknie konsoli, aby wyłączyć klienta.  
  
 Usługa może zostać powiadomiona o błędach <xref:System.ServiceModel.Dispatcher.IErrorHandler>autoryzacji, implementując plik . Aby uzyskać informacje na temat wdrażania, `IErrorHandler`zobacz [Rozszerzanie kontroli nad obsługą błędów i raportowaniem.](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  

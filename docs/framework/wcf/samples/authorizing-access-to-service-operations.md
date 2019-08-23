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
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="ea4f9-102">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="ea4f9-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="ea4f9-103">Ten przykład pokazuje, <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) jak używać > ServiceAuthorization, aby umożliwić korzystanie z atrybutu w celu autoryzacji dostępu do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="ea4f9-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="ea4f9-105">Usługa i klient są konfigurowane przy użyciu [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ea4f9-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="ea4f9-106">`Message` `clientCredentialType`Atrybut> zabezpieczeń został ustawiony na wartość i został ustawiony na `Windows`. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `mode`</span><span class="sxs-lookup"><span data-stu-id="ea4f9-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="ea4f9-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Stosuje się do każdej metody usługi i służy do ograniczania dostępu do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="ea4f9-108">Obiekt wywołujący musi być administratorem systemu Windows, aby uzyskać dostęp do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="ea4f9-109">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ea4f9-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea4f9-110">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ea4f9-111">Plik konfiguracji usługi używa [ \<> ServiceAuthorization](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) , aby ustawić `principalPermissionMode` atrybut:</span><span class="sxs-lookup"><span data-stu-id="ea4f9-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="ea4f9-112">`principalPermissionMode` Ustawienie do `UseWindowsGroups` umożliwia Korzystanie<xref:System.Security.Permissions.PrincipalPermissionAttribute> z nazw grup systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="ea4f9-113">Program <xref:System.Security.Permissions.PrincipalPermissionAttribute> jest stosowany do każdej operacji, aby wymagać, aby wywołujący należał do grupy administratorów systemu Windows, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="ea4f9-114">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ea4f9-115">Klient pomyślnie komunikuje się z każdą operacją, jeśli jest uruchomiona przy użyciu konta należącego do grupy Administratorzy; w przeciwnym razie odmowa dostępu.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="ea4f9-116">Aby eksperymentować z błędem autoryzacji, uruchom klienta w ramach konta, które nie jest częścią grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="ea4f9-117">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="ea4f9-118">Usługa może być powiadamiana o błędach autoryzacji przez implementację <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="ea4f9-119">Zobacz [Rozszerzanie kontroli nad obsługą błędów i raportowanie](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informacji o `IErrorHandler`wdrażaniu.</span><span class="sxs-lookup"><span data-stu-id="ea4f9-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea4f9-120">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="ea4f9-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ea4f9-121">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea4f9-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ea4f9-122">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea4f9-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ea4f9-123">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea4f9-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

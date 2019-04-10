---
title: Autoryzowanie dostępu do operacji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 857e1ebe21dcb37764ddf60570a00ec35b205c8b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345797"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="36200-102">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="36200-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="36200-103">W tym przykładzie przedstawiono sposób użycia [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu do autoryzowania dostępu do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="36200-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="36200-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="36200-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="36200-105">Usługi i klienta są konfigurowane za pomocą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="36200-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="36200-106">`mode` Atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) został ustawiony na `Message` i `clientCredentialType` został ustawiony na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="36200-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="36200-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowane do każdej metody usługi i używany do ograniczania dostępu do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="36200-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="36200-108">Obiekt wywołujący musi być Windows administratorowi dostęp do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="36200-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="36200-109">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="36200-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36200-110">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="36200-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="36200-111">Korzysta z pliku konfiguracji usługi [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) można ustawić `principalPermissionMode` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="36200-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="36200-112">Ustawienie `principalPermissionMode` do `UseWindowsGroups` umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> na podstawie nazw grupy Windows.</span><span class="sxs-lookup"><span data-stu-id="36200-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="36200-113"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowany do każdej operacji, aby wymagać obiekt wywołujący, aby być częścią grupy administratorów Windows, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="36200-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="36200-114">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="36200-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="36200-115">Klient pomyślnie komunikuje się z każdej operacji, jeśli jest uruchomiony przy użyciu konta należącego do grupy Administratorzy; w przeciwnym razie odmowa dostępu.</span><span class="sxs-lookup"><span data-stu-id="36200-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="36200-116">Aby eksperymentować z błąd autoryzacji, uruchom klienta przy użyciu konta, które nie jest częścią grupy administratorów.</span><span class="sxs-lookup"><span data-stu-id="36200-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="36200-117">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="36200-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="36200-118">Usługa może zostać poinformowany o błędy autoryzacji przez zaimplementowanie <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="36200-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="36200-119">Zobacz [rozszerzanie kontroli nad obsługę błędów i raportowanie](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informacji o implementowaniu `IErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="36200-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="36200-120">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="36200-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="36200-121">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="36200-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="36200-122">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="36200-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="36200-123">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="36200-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

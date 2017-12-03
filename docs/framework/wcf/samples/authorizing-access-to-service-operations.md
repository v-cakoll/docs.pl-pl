---
title: "Autoryzowanie dostępu do operacji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2bcd3739cebf852e69cc2551350a83e247274e0a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="ade93-102">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="ade93-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="ade93-103">W tym przykładzie przedstawiono sposób użycia [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybut do autoryzowania dostępu do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="ade93-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="ade93-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="ade93-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="ade93-105">Usługa i klient skonfigurowanych za pomocą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ade93-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="ade93-106">`mode` Atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) została ustawiona jako `Message` i `clientCredentialType` została ustawiona jako `Windows`.</span><span class="sxs-lookup"><span data-stu-id="ade93-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="ade93-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowane do każdej metody usługi i używany do ograniczania dostępu do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="ade93-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="ade93-108">Obiekt wywołujący musi być kontem administratora systemu Windows można uzyskać dostępu do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="ade93-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="ade93-109">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ade93-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ade93-110">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ade93-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ade93-111">Plik konfiguracji usługi używa [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) można ustawić `principalPermissionMode` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="ade93-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="ade93-112">Ustawienie `principalPermissionMode` do `UseWindowsGroups` umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> na podstawie nazw grupy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ade93-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="ade93-113"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowany do każdej operacji wymagające wywołującego należeć do grupy Administratorzy systemu Windows, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="ade93-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="ade93-114">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ade93-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ade93-115">Klient pomyślnie komunikuje się z każdej operacji Jeśli została uruchomiona przy użyciu konta należącego do grupy Administratorzy; w przeciwnym razie nastąpi odmowa dostępu.</span><span class="sxs-lookup"><span data-stu-id="ade93-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="ade93-116">Eksperymentować błąd autoryzacji, uruchom klienta przy użyciu konta, które nie należą do grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="ade93-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="ade93-117">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="ade93-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="ade93-118">Usługa może być powiadamiany o błędami autoryzacji zaimplementowanie <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="ade93-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="ade93-119">Zobacz [rozszerzanie kontroli nad błąd obsługi i raportowania](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informacji o implementacji `IErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="ade93-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ade93-120">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="ade93-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ade93-121">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ade93-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ade93-122">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ade93-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ade93-123">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ade93-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade93-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ade93-124">See Also</span></span>

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
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="0a76a-102">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="0a76a-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="0a76a-103">W tym przykładzie pokazano, jak używać [ \<serviceAuthorization>,](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) aby włączyć korzystanie z atrybutu <xref:System.Security.Permissions.PrincipalPermissionAttribute> do autoryzowania dostępu do operacji serwisowych.</span><span class="sxs-lookup"><span data-stu-id="0a76a-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="0a76a-104">Ten przykład jest oparty na próbce [Wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="0a76a-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="0a76a-105">Usługa i klient są konfigurowane przy użyciu [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0a76a-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="0a76a-106">Atrybut `mode` [ \<>zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) został ustawiony `Message` na . `clientCredentialType` `Windows`</span><span class="sxs-lookup"><span data-stu-id="0a76a-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="0a76a-107">Jest <xref:System.Security.Permissions.PrincipalPermissionAttribute> stosowany do każdej metody usługi i służy do ograniczania dostępu do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="0a76a-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="0a76a-108">Wywołujący musi być administratorem systemu Windows, aby uzyskać dostęp do każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="0a76a-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="0a76a-109">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="0a76a-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a76a-110">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0a76a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0a76a-111">Plik konfiguracji usługi używa [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do `principalPermissionMode` ustawienia atrybutu:</span><span class="sxs-lookup"><span data-stu-id="0a76a-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="0a76a-112">`principalPermissionMode` Ustawienie, `UseWindowsGroups` aby włączyć <xref:System.Security.Permissions.PrincipalPermissionAttribute> korzystanie z oparte na nazwach grup systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0a76a-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="0a76a-113">Jest <xref:System.Security.Permissions.PrincipalPermissionAttribute> stosowany do każdej operacji, aby wymagać, aby wywołujący być częścią grupy administratorów systemu Windows, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0a76a-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="0a76a-114">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="0a76a-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0a76a-115">Klient pomyślnie komunikuje się z każdą operacją, jeśli działa na koncie należącym do grupy Administratorzy; w przeciwnym razie odmowa dostępu.</span><span class="sxs-lookup"><span data-stu-id="0a76a-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="0a76a-116">Aby eksperymentować z niepowodzeniem autoryzacji, uruchom klienta na koncie, które nie jest częścią grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="0a76a-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="0a76a-117">Naciśnij klawisz ENTER w oknie konsoli, aby wyłączyć klienta.</span><span class="sxs-lookup"><span data-stu-id="0a76a-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="0a76a-118">Usługa może zostać powiadomiona o błędach <xref:System.ServiceModel.Dispatcher.IErrorHandler>autoryzacji, implementując plik .</span><span class="sxs-lookup"><span data-stu-id="0a76a-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="0a76a-119">Aby uzyskać informacje na temat wdrażania, `IErrorHandler`zobacz [Rozszerzanie kontroli nad obsługą błędów i raportowaniem.](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="0a76a-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0a76a-120">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="0a76a-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0a76a-121">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a76a-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0a76a-122">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a76a-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0a76a-123">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a76a-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

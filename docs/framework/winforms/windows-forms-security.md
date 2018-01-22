---
title: Zabezpieczenia formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bd9b87fdfa54a6f9bf53e4fa897106257b4c625
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-security"></a><span data-ttu-id="95af3-102">Zabezpieczenia formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95af3-102">Windows Forms Security</span></span>
<span data-ttu-id="95af3-103">Formularze systemu Windows funkcji modelu zabezpieczeń, które jest oparte na kodzie (zabezpieczenia są ustawione przez kod, niezależnie od kodu użytkownika dla poziomów).</span><span class="sxs-lookup"><span data-stu-id="95af3-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="95af3-104">Jest to oprócz żadnych schematów zabezpieczeń, które mogą być spełnione już na komputerze.</span><span class="sxs-lookup"><span data-stu-id="95af3-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="95af3-105">Mogą to być te przeglądarki (np. na podstawie strefy zabezpieczeń programu Internet Explorer) lub system operacyjny (na przykład zabezpieczenia oparte na dostęp do poświadczeń systemu Windows NT).</span><span class="sxs-lookup"><span data-stu-id="95af3-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95af3-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="95af3-106">In This Section</span></span>  
 [<span data-ttu-id="95af3-107">Przegląd zabezpieczeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95af3-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="95af3-108">Krótko opisano model zabezpieczeń .NET Framework i podstawowe kroki niezbędne do zapewnienia formularzy systemu Windows w aplikacji to bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="95af3-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="95af3-109">Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95af3-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="95af3-110">Opisuje sposób dostępu do plików i danych w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="95af3-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="95af3-111">Bezpieczniejsze drukowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95af3-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="95af3-112">Opisuje sposób uzyskiwać dostęp do funkcji drukowania w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="95af3-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="95af3-113">Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95af3-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="95af3-114">W tym artykule opisano wykonywania manipulowanie okna, korzystanie ze Schowka i wykonywania wywołań do kodu niezarządzanego w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="95af3-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="95af3-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="95af3-115">Related Sections</span></span>  
 [<span data-ttu-id="95af3-116">NIB: Domyślnych zasad zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="95af3-116">NIB: Default Security Policy</span></span>](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 <span data-ttu-id="95af3-117">Zawiera listę domyślnych uprawnień w zestawy uprawnień pełnego zaufania, lokalny Intranet i Internet.</span><span class="sxs-lookup"><span data-stu-id="95af3-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 [<span data-ttu-id="95af3-118">NIB: Administrowanie zasadami zabezpieczeń Ogólne</span><span class="sxs-lookup"><span data-stu-id="95af3-118">NIB: General Security Policy Administration</span></span>](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 <span data-ttu-id="95af3-119">Zawiera informacje dotyczące administrowania zasadami zabezpieczeń .NET Framework i podnoszenia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="95af3-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="95af3-120">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="95af3-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="95af3-121">Omówiono niektóre środowiska.NET Framework uprawnienia, które umożliwia systemu zabezpieczeń obejść.</span><span class="sxs-lookup"><span data-stu-id="95af3-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="95af3-122">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="95af3-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="95af3-123">Linki do tematów dotyczących najlepszych rozwiązań dotyczących bezpiecznego pisanie kodu dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95af3-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 [<span data-ttu-id="95af3-124">NIB: Żądanie uprawnień</span><span class="sxs-lookup"><span data-stu-id="95af3-124">NIB: Requesting Permissions</span></span>](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 <span data-ttu-id="95af3-125">W tym artykule omówiono korzystanie z atrybutów, aby umożliwić środowiska uruchomieniowego wiedzieć, jakie uprawnienia kodu musi być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="95af3-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="95af3-126">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="95af3-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="95af3-127">Linki do tematów, które obejmuje podstawowych kwestii zabezpieczeń kodu.</span><span class="sxs-lookup"><span data-stu-id="95af3-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="95af3-128">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="95af3-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="95af3-129">W tym artykule omówiono podstawowe informacje dotyczące pracy z programu .NET Framework zasady zabezpieczeń w czasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="95af3-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 [<span data-ttu-id="95af3-130">NIB: Określanie, kiedy należy zmodyfikować zasady zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="95af3-130">NIB: Determining When to Modify Security Policy</span></span>](http://msdn.microsoft.com/library/af749b17-e461-409d-84b9-a3d44789db16)  
 <span data-ttu-id="95af3-131">Wyjaśniono sposób określania, kiedy aplikacje muszą różnią się od domyślnych zasad zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="95af3-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 [<span data-ttu-id="95af3-132">NIB: Wdrażanie zasad zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="95af3-132">NIB: Deploying Security Policy</span></span>](http://msdn.microsoft.com/library/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 <span data-ttu-id="95af3-133">W tym artykule omówiono najlepsze sposób wdrażania zmian zasad zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="95af3-133">Discusses the best manner for deploying security policy changes.</span></span>

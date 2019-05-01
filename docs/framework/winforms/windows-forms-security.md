---
title: Zabezpieczenia formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: f64d5ef2e9bb0e977b4c007e8c5109ac0c331a84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799375"
---
# <a name="windows-forms-security"></a><span data-ttu-id="d7c6f-102">Zabezpieczenia formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d7c6f-102">Windows Forms Security</span></span>
<span data-ttu-id="d7c6f-103">Formularze Windows oferuje model zabezpieczeń, który jest oparty na kodzie (zabezpieczeń ustawionych poziomów dla kodu, niezależnie od użytkownika, uruchamiając kod).</span><span class="sxs-lookup"><span data-stu-id="d7c6f-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="d7c6f-104">Jest to oprócz schematów zabezpieczeń, które mogą być spełnione już na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="d7c6f-105">Mogą to być te w przeglądarce (na przykład na podstawie strefy zabezpieczeń dostępnych w programie Internet Explorer) lub systemu operacyjnego (na przykład opartego na poświadczeniu zabezpieczenia systemu Windows NT).</span><span class="sxs-lookup"><span data-stu-id="d7c6f-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7c6f-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d7c6f-106">In This Section</span></span>  
 [<span data-ttu-id="d7c6f-107">Przegląd zabezpieczeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7c6f-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="d7c6f-108">Zawiera krótkie opisy, że model zabezpieczeń .NET Framework i podstawowe kroki niezbędne do zapewnienia formularzy Windows w aplikacji są bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="d7c6f-109">Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7c6f-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="d7c6f-110">Opisuje sposób dostępu do plików i danych w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="d7c6f-111">Bezpieczniejsze drukowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7c6f-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="d7c6f-112">Zawiera opis sposobu uzyskania dostępu do funkcji drukowania w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="d7c6f-113">Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7c6f-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="d7c6f-114">W tym artykule opisano przeprowadzanie manipulacji okna: Korzystanie ze Schowka i wykonywania wywołań do kodu niezarządzanego w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7c6f-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d7c6f-115">Related Sections</span></span>  
 <span data-ttu-id="d7c6f-116">[Domyślnych zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d7c6f-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="d7c6f-117">Wyświetla listę domyślne uprawnienia przyznane w zestawy uprawnień pełnego zaufania, lokalny Intranet i Internet.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="d7c6f-118">[Ogólne zasady zabezpieczeń administracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d7c6f-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="d7c6f-119">Zawiera informacje dotyczące administrowania zasadami zabezpieczeń .NET Framework i podnoszenia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="d7c6f-120">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="d7c6f-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="d7c6f-121">W tym artykule omówiono, niektóre środowiska.NET Framework uprawnienia, które umożliwia system zabezpieczeń obejść.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="d7c6f-122">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="d7c6f-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="d7c6f-123">Zawiera łącza do tematów, które opisują najlepsze rozwiązania dotyczące bezpiecznego pisanie kodu dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="d7c6f-124">[Żądanie uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d7c6f-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="d7c6f-125">W tym artykule omówiono używanie atrybutów, aby umożliwić środowiska uruchomieniowego wiedzieć, jakie uprawnienia, kod musi zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="d7c6f-126">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d7c6f-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="d7c6f-127">Zawiera łącza do tematów, które obejmują podstawowe aspekty zabezpieczeń kodu.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="d7c6f-128">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="d7c6f-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="d7c6f-129">W tym artykule omówiono podstawowe informacje dotyczące pracy z .NET Framework, zasady zabezpieczeń w czasie uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="d7c6f-130">[Ustalanie, kiedy modyfikowania zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d7c6f-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="d7c6f-131">Wyjaśnia, jak ustalić, kiedy trzeba rozdzielić z domyślnych zasad zabezpieczeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="d7c6f-132">[Wdrażanie zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d7c6f-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="d7c6f-133">W tym artykule omówiono najlepsze sposób wdrażania zmiany zasad zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d7c6f-133">Discusses the best manner for deploying security policy changes.</span></span>

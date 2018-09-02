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
ms.openlocfilehash: 75016e9e04cf47782add18c87f7c677931743a4e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397253"
---
# <a name="windows-forms-security"></a><span data-ttu-id="570ab-102">Zabezpieczenia formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="570ab-102">Windows Forms Security</span></span>
<span data-ttu-id="570ab-103">Formularze Windows oferuje model zabezpieczeń, który jest oparty na kodzie (zabezpieczeń ustawionych poziomów dla kodu, niezależnie od użytkownika, uruchamiając kod).</span><span class="sxs-lookup"><span data-stu-id="570ab-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="570ab-104">Jest to oprócz schematów zabezpieczeń, które mogą być spełnione już na komputerze.</span><span class="sxs-lookup"><span data-stu-id="570ab-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="570ab-105">Mogą to być te w przeglądarce (na przykład na podstawie strefy zabezpieczeń dostępnych w programie Internet Explorer) lub systemu operacyjnego (na przykład opartego na poświadczeniu zabezpieczenia systemu Windows NT).</span><span class="sxs-lookup"><span data-stu-id="570ab-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="570ab-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="570ab-106">In This Section</span></span>  
 [<span data-ttu-id="570ab-107">Przegląd zabezpieczeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="570ab-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="570ab-108">Zawiera krótkie opisy, że model zabezpieczeń .NET Framework i podstawowe kroki niezbędne do zapewnienia formularzy Windows w aplikacji są bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="570ab-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="570ab-109">Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="570ab-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="570ab-110">Opisuje sposób dostępu do plików i danych w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="570ab-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="570ab-111">Bezpieczniejsze drukowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="570ab-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="570ab-112">Zawiera opis sposobu uzyskania dostępu do funkcji drukowania w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="570ab-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="570ab-113">Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="570ab-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="570ab-114">W tym artykule opisano przeprowadzanie manipulacji okna: Korzystanie ze Schowka i wykonywania wywołań do kodu niezarządzanego w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="570ab-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="570ab-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="570ab-115">Related Sections</span></span>  
 [<span data-ttu-id="570ab-116">NIB: Domyślnych zasad zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="570ab-116">NIB: Default Security Policy</span></span>](https://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 <span data-ttu-id="570ab-117">Wyświetla listę domyślne uprawnienia przyznane w zestawy uprawnień pełnego zaufania, lokalny Intranet i Internet.</span><span class="sxs-lookup"><span data-stu-id="570ab-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 [<span data-ttu-id="570ab-118">NIB: Administrowanie zasadami zabezpieczeń Ogólne</span><span class="sxs-lookup"><span data-stu-id="570ab-118">NIB: General Security Policy Administration</span></span>](https://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 <span data-ttu-id="570ab-119">Zawiera informacje dotyczące administrowania zasadami zabezpieczeń .NET Framework i podnoszenia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="570ab-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="570ab-120">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="570ab-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="570ab-121">W tym artykule omówiono, niektóre środowiska.NET Framework uprawnienia, które umożliwia system zabezpieczeń obejść.</span><span class="sxs-lookup"><span data-stu-id="570ab-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="570ab-122">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="570ab-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="570ab-123">Zawiera łącza do tematów, które opisują najlepsze rozwiązania dotyczące bezpiecznego pisanie kodu dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="570ab-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 [<span data-ttu-id="570ab-124">NIB: Żądanie uprawnień</span><span class="sxs-lookup"><span data-stu-id="570ab-124">NIB: Requesting Permissions</span></span>](https://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 <span data-ttu-id="570ab-125">W tym artykule omówiono używanie atrybutów, aby umożliwić środowiska uruchomieniowego wiedzieć, jakie uprawnienia, kod musi zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="570ab-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="570ab-126">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="570ab-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="570ab-127">Zawiera łącza do tematów, które obejmują podstawowe aspekty zabezpieczeń kodu.</span><span class="sxs-lookup"><span data-stu-id="570ab-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="570ab-128">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="570ab-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="570ab-129">W tym artykule omówiono podstawowe informacje dotyczące pracy z .NET Framework, zasady zabezpieczeń w czasie uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="570ab-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 [<span data-ttu-id="570ab-130">NIB: Ustalanie, kiedy modyfikowania zasad zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="570ab-130">NIB: Determining When to Modify Security Policy</span></span>](https://msdn.microsoft.com/library/af749b17-e461-409d-84b9-a3d44789db16)  
 <span data-ttu-id="570ab-131">Wyjaśnia, jak ustalić, kiedy trzeba rozdzielić z domyślnych zasad zabezpieczeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="570ab-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 [<span data-ttu-id="570ab-132">NIB: Wdrażanie zasad zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="570ab-132">NIB: Deploying Security Policy</span></span>](https://msdn.microsoft.com/library/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 <span data-ttu-id="570ab-133">W tym artykule omówiono najlepsze sposób wdrażania zmiany zasad zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="570ab-133">Discusses the best manner for deploying security policy changes.</span></span>

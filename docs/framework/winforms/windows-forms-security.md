---
title: Zabezpieczenia
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: a3debf487b9b2a04277d9ce3007f28662fa4899e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734493"
---
# <a name="windows-forms-security"></a><span data-ttu-id="2eb05-102">Zabezpieczenia formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2eb05-102">Windows Forms Security</span></span>
<span data-ttu-id="2eb05-103">Windows Forms funkcje modelu zabezpieczeń, który jest oparty na kodzie (poziomy zabezpieczeń są ustawiane dla kodu, niezależnie od tego, czy użytkownik uruchomił kod).</span><span class="sxs-lookup"><span data-stu-id="2eb05-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="2eb05-104">Jest to uzupełnienie wszelkich schematów zabezpieczeń, które mogą znajdować się już w systemie komputerowym.</span><span class="sxs-lookup"><span data-stu-id="2eb05-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="2eb05-105">Mogą one obejmować te w przeglądarce (takie jak zabezpieczenia oparte na strefach dostępne w programie Internet Explorer) lub systemu operacyjnego (na przykład zabezpieczenia oparte na poświadczeniach systemu Windows NT).</span><span class="sxs-lookup"><span data-stu-id="2eb05-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2eb05-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2eb05-106">In This Section</span></span>  
 [<span data-ttu-id="2eb05-107">Przegląd zabezpieczeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eb05-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="2eb05-108">Krótko objaśnia model zabezpieczeń .NET Framework i podstawowe kroki, które należy wykonać, aby zapewnić bezpieczeństwo Windows Forms w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2eb05-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="2eb05-109">Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eb05-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="2eb05-110">Opisuje sposób uzyskiwania dostępu do plików i danych w środowisku częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="2eb05-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="2eb05-111">Bezpieczniejsze drukowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eb05-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="2eb05-112">Opisuje sposób uzyskiwania dostępu do funkcji drukowania w środowisku częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="2eb05-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="2eb05-113">Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eb05-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="2eb05-114">Opisuje wykonywanie manipulowania oknem przy użyciu Schowka i wykonywanie wywołań do kodu niezarządzanego w środowisku częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="2eb05-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2eb05-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2eb05-115">Related Sections</span></span>  
 <span data-ttu-id="2eb05-116">[Domyślne zasady zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2eb05-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="2eb05-117">Wyświetla listę domyślnych uprawnień udzielonych w ramach pełnego zaufania, lokalnego intranetu i zestawów uprawnień internetowych.</span><span class="sxs-lookup"><span data-stu-id="2eb05-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="2eb05-118">[Ogólne administrowanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2eb05-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="2eb05-119">Zawiera informacje o administrowaniu zasadami zabezpieczeń .NET Framework i podwyższeniem poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2eb05-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="2eb05-120">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="2eb05-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="2eb05-121">W tym artykule omówiono niektóre uprawnienia the.NET Framework, które mogą potencjalnie pozwolić na obejście systemu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2eb05-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="2eb05-122">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="2eb05-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="2eb05-123">Linki do tematów, które opisują najlepsze rozwiązania dotyczące bezpiecznego pisania kodu w odniesieniu do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2eb05-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="2eb05-124">[Żądanie uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2eb05-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="2eb05-125">W tym artykule omówiono użycie atrybutów w celu uzyskania informacji o uprawnieniach wymaganych do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="2eb05-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="2eb05-126">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2eb05-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="2eb05-127">Linki do tematów obejmujących podstawowe aspekty zabezpieczeń kodu.</span><span class="sxs-lookup"><span data-stu-id="2eb05-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="2eb05-128">Podstawowe informacje o zabezpieczeniach dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="2eb05-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="2eb05-129">W tym artykule omówiono podstawowe informacje dotyczące pracy z .NET Framework zasadami zabezpieczeń czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2eb05-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="2eb05-130">[Ustalanie, kiedy należy zmodyfikować zasady zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2eb05-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="2eb05-131">Wyjaśnia, jak ustalić, kiedy aplikacje muszą rozróżnić się od domyślnych zasad zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2eb05-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="2eb05-132">[Wdrażanie zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2eb05-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="2eb05-133">W tym artykule omówiono najlepszy sposób wdrażania zmian zasad zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2eb05-133">Discusses the best manner for deploying security policy changes.</span></span>

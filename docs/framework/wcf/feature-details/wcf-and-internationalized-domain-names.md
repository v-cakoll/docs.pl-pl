---
title: "Architektura WCF i międzynarodowe nazwy domen"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cae287ab440115b15f6c26209a3d40bee4f9703b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="96912-102">Architektura WCF i międzynarodowe nazwy domen</span><span class="sxs-lookup"><span data-stu-id="96912-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="96912-103">Dodano obsługę umożliwiające usługi WCF z domeny nazwy (IDN).</span><span class="sxs-lookup"><span data-stu-id="96912-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="96912-104">Międzynarodowych nazw domen jest nazwą domeny, który zawiera znaki spoza zestawu ASCII.</span><span class="sxs-lookup"><span data-stu-id="96912-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="96912-105">Ta obsługa obejmuje to możliwość hostowanie usługi WCF z nazwą IDN i klienta WCF do komunikowania się z usługą sieci web z nazwą IDN.</span><span class="sxs-lookup"><span data-stu-id="96912-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="96912-106">System.Uri i IDN</span><span class="sxs-lookup"><span data-stu-id="96912-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="96912-107"><xref:System.Uri>ma dwie właściwości <xref:System.Uri.Host%2A> i <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="96912-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="96912-108">Te właściwości zawierają wartości Unicode lub ciąg Punycode, w zależności od ustawień konfiguracji IDN.</span><span class="sxs-lookup"><span data-stu-id="96912-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="96912-109">IDN jest włączone w pliku konfiguracji aplikacji przy użyciu następującego kodu XML</span><span class="sxs-lookup"><span data-stu-id="96912-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="96912-110">\<Idn > element zawiera włączony atrybut, który może być ustawione na jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="96912-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="96912-111">"None"</span><span class="sxs-lookup"><span data-stu-id="96912-111">"None"</span></span>  
  
2.  <span data-ttu-id="96912-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="96912-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="96912-113">"Wszystkie"</span><span class="sxs-lookup"><span data-stu-id="96912-113">"All"</span></span>  
  
 <span data-ttu-id="96912-114">Ustawienie IDN ma wartość "None", ma konwersji są wykonywane przez Uri.Host lub Uri.DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="96912-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="96912-115">Gdy ustawienie IDN ma wartość "Wszystkie", identyfikator uri. Host pozostaje Unicode i identyfikatora uri. DnsSafeHost jest konwertowana na ciąg Punycode.</span><span class="sxs-lookup"><span data-stu-id="96912-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="96912-116">Jeśli ustawienie IDN jest równa "AllExceptIntranet", identyfikator uri. DnsSafeHost jest konwertowana na ciąg Punycode w przypadku adresów internetowych i pozostaje Unicode intranetowe adresy.</span><span class="sxs-lookup"><span data-stu-id="96912-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="96912-117">To ustawienie jest ważne w przypadku poprawne rozpoznawanie nazwy DNS.</span><span class="sxs-lookup"><span data-stu-id="96912-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="96912-118">Uwaga: to ustawienie nie jest wymagane do skonfigurowania dla systemu Windows 8 i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="96912-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="96912-119">Należy nigdy nie kodowane adresu przy użyciu Punycode.</span><span class="sxs-lookup"><span data-stu-id="96912-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="96912-120">Usługi WCF przekonwertuje go na podstawie ustawień konfiguracji, które należy zastosować.</span><span class="sxs-lookup"><span data-stu-id="96912-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="96912-121">Podczas dodawania znaków Unicode do applicationHost.exe.config, Zapisz plik przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="96912-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96912-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96912-122">See Also</span></span>  
 [<span data-ttu-id="96912-123">System.Uri</span><span class="sxs-lookup"><span data-stu-id="96912-123">System.Uri</span></span>](http://msdn.microsoft.com/library/system.uri.aspx)

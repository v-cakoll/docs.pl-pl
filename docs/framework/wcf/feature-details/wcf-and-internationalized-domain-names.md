---
title: Architektura WCF i międzynarodowe nazwy domen
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: c53c22e388ec352b1275018c0b945c9608565084
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335384"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="261ca-102">Architektura WCF i międzynarodowe nazwy domen</span><span class="sxs-lookup"><span data-stu-id="261ca-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="261ca-103">Dodano obsługę do obsługi usług WCF za pomocą nazw międzynarodowych domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="261ca-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="261ca-104">Międzynarodowa nazwa domeny jest nazwa domeny, który zawiera znaki spoza zestawu ASCII.</span><span class="sxs-lookup"><span data-stu-id="261ca-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="261ca-105">Ta obsługa obejmuje możliwość hostowanie usługi WCF przy użyciu nazwy IDN i klienta programu WCF na komunikowanie się z usługą sieci web o nazwie IDN.</span><span class="sxs-lookup"><span data-stu-id="261ca-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="261ca-106">System.Uri i IDN</span><span class="sxs-lookup"><span data-stu-id="261ca-106">System.Uri and IDN</span></span>  
 <xref:System.Uri> <span data-ttu-id="261ca-107">ma dwie właściwości <xref:System.Uri.Host%2A> i <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="261ca-107">has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="261ca-108">Te właściwości zawierają wartości Unicode lub Punycode, w zależności od ustawień konfiguracji IDN.</span><span class="sxs-lookup"><span data-stu-id="261ca-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="261ca-109">IDN jest włączone w pliku konfiguracji aplikacji przy użyciu następujący kod XML</span><span class="sxs-lookup"><span data-stu-id="261ca-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="261ca-110">\<Idn > element zawiera atrybut włączony, którą można ustawić na jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="261ca-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1. <span data-ttu-id="261ca-111">"None"</span><span class="sxs-lookup"><span data-stu-id="261ca-111">"None"</span></span>  
  
2. <span data-ttu-id="261ca-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="261ca-112">"AllExceptIntranet"</span></span>  
  
3. <span data-ttu-id="261ca-113">"Wszystkie"</span><span class="sxs-lookup"><span data-stu-id="261ca-113">"All"</span></span>  
  
 <span data-ttu-id="261ca-114">Gdy ustawienie IDN ma wartość "None", nie konwersje są wykonywane przez Uri.Host lub Uri.DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="261ca-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="261ca-115">Jeśli ustawienie IDN jest równa "All", identyfikator uri. Host pozostaje Unicode i identyfikatora uri. DnsSafeHost jest konwertowana na ciąg Punycode.</span><span class="sxs-lookup"><span data-stu-id="261ca-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="261ca-116">Jeśli ustawienie IDN, jest równa "AllExceptIntranet", identyfikator uri. DnsSafeHost jest konwertowana na ciąg Punycode w przypadku adresów internetowych i pozostaje Unicode dla adresów w sieci intranet.</span><span class="sxs-lookup"><span data-stu-id="261ca-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="261ca-117">To ustawienie jest ważne dla poprawnego rozpoznawania nazw DNS.</span><span class="sxs-lookup"><span data-stu-id="261ca-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="261ca-118">Należy pamiętać, że to ustawienie nie jest wymagane do skonfigurowania dla systemu Windows 8 i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="261ca-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="261ca-119">Powinno nigdy trwale kodować adresu przy użyciu Punycode.</span><span class="sxs-lookup"><span data-stu-id="261ca-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="261ca-120">Usługi WCF przekonwertuje go na podstawie ustawień konfiguracji, które należy zastosować.</span><span class="sxs-lookup"><span data-stu-id="261ca-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="261ca-121">Podczas dodawania znaków Unicode do applicationHost.exe.config, Zapisz plik przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="261ca-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261ca-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="261ca-122">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>

---
title: Architektura WCF i międzynarodowe nazwy domen
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: c166f497117314dd8cea3b04b9b1072203374c52
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112609"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="07a91-102">Architektura WCF i międzynarodowe nazwy domen</span><span class="sxs-lookup"><span data-stu-id="07a91-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="07a91-103">Dodano obsługę do obsługi usług WCF za pomocą nazw międzynarodowych domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="07a91-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="07a91-104">Międzynarodowa nazwa domeny jest nazwa domeny, który zawiera znaki spoza zestawu ASCII.</span><span class="sxs-lookup"><span data-stu-id="07a91-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="07a91-105">Ta obsługa obejmuje możliwość hostowanie usługi WCF przy użyciu nazwy IDN i klienta programu WCF na komunikowanie się z usługą sieci web o nazwie IDN.</span><span class="sxs-lookup"><span data-stu-id="07a91-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="07a91-106">System.Uri i IDN</span><span class="sxs-lookup"><span data-stu-id="07a91-106">System.Uri and IDN</span></span>  
 <xref:System.Uri> <span data-ttu-id="07a91-107">ma dwie właściwości <xref:System.Uri.Host%2A> i <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="07a91-107">has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="07a91-108">Te właściwości zawierają wartości Unicode lub Punycode, w zależności od ustawień konfiguracji IDN.</span><span class="sxs-lookup"><span data-stu-id="07a91-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="07a91-109">IDN jest włączone w pliku konfiguracji aplikacji przy użyciu następujący kod XML</span><span class="sxs-lookup"><span data-stu-id="07a91-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="07a91-110">\<Idn > element zawiera atrybut włączony, którą można ustawić na jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="07a91-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="07a91-111">"None"</span><span class="sxs-lookup"><span data-stu-id="07a91-111">"None"</span></span>  
  
2.  <span data-ttu-id="07a91-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="07a91-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="07a91-113">"Wszystkie"</span><span class="sxs-lookup"><span data-stu-id="07a91-113">"All"</span></span>  
  
 <span data-ttu-id="07a91-114">Gdy ustawienie IDN ma wartość "None", nie konwersje są wykonywane przez Uri.Host lub Uri.DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="07a91-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="07a91-115">Jeśli ustawienie IDN jest równa "All", identyfikator uri. Host pozostaje Unicode i identyfikatora uri. DnsSafeHost jest konwertowana na ciąg Punycode.</span><span class="sxs-lookup"><span data-stu-id="07a91-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="07a91-116">Jeśli ustawienie IDN, jest równa "AllExceptIntranet", identyfikator uri. DnsSafeHost jest konwertowana na ciąg Punycode w przypadku adresów internetowych i pozostaje Unicode dla adresów w sieci intranet.</span><span class="sxs-lookup"><span data-stu-id="07a91-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="07a91-117">To ustawienie jest ważne dla poprawnego rozpoznawania nazw DNS.</span><span class="sxs-lookup"><span data-stu-id="07a91-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="07a91-118">Należy pamiętać, że to ustawienie nie jest wymagane do skonfigurowania dla systemu Windows 8 i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="07a91-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="07a91-119">Powinno nigdy trwale kodować adresu przy użyciu Punycode.</span><span class="sxs-lookup"><span data-stu-id="07a91-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="07a91-120">Usługi WCF przekonwertuje go na podstawie ustawień konfiguracji, które należy zastosować.</span><span class="sxs-lookup"><span data-stu-id="07a91-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="07a91-121">Podczas dodawania znaków Unicode do applicationHost.exe.config, Zapisz plik przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="07a91-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a91-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07a91-122">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>

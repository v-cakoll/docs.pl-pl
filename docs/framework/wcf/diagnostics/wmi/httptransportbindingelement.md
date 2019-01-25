---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 2376a0ec25539b97a37b1827e3e4c148eb8d5838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610776"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="023a5-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="023a5-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="023a5-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="023a5-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="023a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="023a5-104">Syntax</span></span>  
  
```csharp
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="023a5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="023a5-105">Methods</span></span>  
 <span data-ttu-id="023a5-106">Klasa HttpTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="023a5-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="023a5-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="023a5-107">Properties</span></span>  
 <span data-ttu-id="023a5-108">Klasa HttpTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="023a5-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="023a5-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="023a5-109">AllowCookies</span></span>  
 <span data-ttu-id="023a5-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="023a5-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="023a5-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-112">Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="023a5-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="023a5-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="023a5-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="023a5-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="023a5-114">Data type: string</span></span>  
  
 <span data-ttu-id="023a5-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-116">Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez odbiornik HTTP.</span><span class="sxs-lookup"><span data-stu-id="023a5-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="023a5-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="023a5-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="023a5-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="023a5-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="023a5-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-120">Wartość, która wskazuje, czy serwery proxy są ignorowane dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="023a5-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="023a5-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="023a5-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="023a5-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="023a5-122">Data type: string</span></span>  
  
 <span data-ttu-id="023a5-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-124">Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="023a5-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="023a5-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="023a5-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="023a5-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="023a5-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="023a5-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-128">Po włączeniu połączeń HTTP pozostają aktywne niezależnie od tego, poziom aktywności.</span><span class="sxs-lookup"><span data-stu-id="023a5-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="023a5-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="023a5-129">MaxBufferSize</span></span>  
 <span data-ttu-id="023a5-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="023a5-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="023a5-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-132">Maksymalny rozmiar puli bufora.</span><span class="sxs-lookup"><span data-stu-id="023a5-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="023a5-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="023a5-133">ProxyAddress</span></span>  
 <span data-ttu-id="023a5-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="023a5-134">Data type: string</span></span>  
  
 <span data-ttu-id="023a5-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-136">Identyfikator URI, który zawiera adres serwera proxy do obsługi żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="023a5-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="023a5-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="023a5-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="023a5-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="023a5-138">Data type: string</span></span>  
  
 <span data-ttu-id="023a5-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-140">Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="023a5-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="023a5-141">obszar</span><span class="sxs-lookup"><span data-stu-id="023a5-141">Realm</span></span>  
 <span data-ttu-id="023a5-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="023a5-142">Data type: string</span></span>  
  
 <span data-ttu-id="023a5-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-144">Obszar uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="023a5-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="023a5-145">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="023a5-145">TransferMode</span></span>  
 <span data-ttu-id="023a5-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="023a5-146">Data type: string</span></span>  
  
 <span data-ttu-id="023a5-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-148">Wartość, która określa, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="023a5-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="023a5-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="023a5-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="023a5-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="023a5-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="023a5-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-152">Wartość, która wskazuje, czy włączone jest niebezpieczne udostępnianie połączenia na serwerze.</span><span class="sxs-lookup"><span data-stu-id="023a5-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="023a5-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="023a5-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="023a5-154">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="023a5-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="023a5-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="023a5-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="023a5-156">Wartość, która wskazuje, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="023a5-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="023a5-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="023a5-157">Requirements</span></span>  
  
|<span data-ttu-id="023a5-158">MOF</span><span class="sxs-lookup"><span data-stu-id="023a5-158">MOF</span></span>|<span data-ttu-id="023a5-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="023a5-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="023a5-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="023a5-160">Namespace</span></span>|<span data-ttu-id="023a5-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="023a5-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="023a5-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="023a5-162">See also</span></span>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

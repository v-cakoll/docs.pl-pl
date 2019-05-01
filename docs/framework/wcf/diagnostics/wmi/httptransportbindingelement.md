---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 5e23342d57621554aaec67c5c568bb75202a9454
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963491"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="85d93-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="85d93-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="85d93-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="85d93-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85d93-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="85d93-105">Metody</span><span class="sxs-lookup"><span data-stu-id="85d93-105">Methods</span></span>  
 <span data-ttu-id="85d93-106">Klasa HttpTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="85d93-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="85d93-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="85d93-107">Properties</span></span>  
 <span data-ttu-id="85d93-108">Klasa HttpTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="85d93-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="85d93-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="85d93-109">AllowCookies</span></span>  
 <span data-ttu-id="85d93-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="85d93-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="85d93-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-112">Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="85d93-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="85d93-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="85d93-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="85d93-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="85d93-114">Data type: string</span></span>  
  
 <span data-ttu-id="85d93-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-116">Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez odbiornik HTTP.</span><span class="sxs-lookup"><span data-stu-id="85d93-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="85d93-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="85d93-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="85d93-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="85d93-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="85d93-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-120">Wartość, która wskazuje, czy serwery proxy są ignorowane dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="85d93-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="85d93-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="85d93-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="85d93-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="85d93-122">Data type: string</span></span>  
  
 <span data-ttu-id="85d93-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-124">Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="85d93-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="85d93-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="85d93-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="85d93-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="85d93-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="85d93-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-128">Po włączeniu połączeń HTTP pozostają aktywne niezależnie od tego, poziom aktywności.</span><span class="sxs-lookup"><span data-stu-id="85d93-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="85d93-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="85d93-129">MaxBufferSize</span></span>  
 <span data-ttu-id="85d93-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="85d93-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="85d93-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-132">Maksymalny rozmiar puli bufora.</span><span class="sxs-lookup"><span data-stu-id="85d93-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="85d93-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="85d93-133">ProxyAddress</span></span>  
 <span data-ttu-id="85d93-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="85d93-134">Data type: string</span></span>  
  
 <span data-ttu-id="85d93-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-136">Identyfikator URI, który zawiera adres serwera proxy do obsługi żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="85d93-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="85d93-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="85d93-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="85d93-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="85d93-138">Data type: string</span></span>  
  
 <span data-ttu-id="85d93-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-140">Schemat uwierzytelniania używany do uwierzytelniania żądań klienta przetwarzanych przez serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="85d93-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="85d93-141">obszar</span><span class="sxs-lookup"><span data-stu-id="85d93-141">Realm</span></span>  
 <span data-ttu-id="85d93-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="85d93-142">Data type: string</span></span>  
  
 <span data-ttu-id="85d93-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-144">Obszar uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="85d93-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="85d93-145">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="85d93-145">TransferMode</span></span>  
 <span data-ttu-id="85d93-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="85d93-146">Data type: string</span></span>  
  
 <span data-ttu-id="85d93-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-148">Wartość, która określa, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="85d93-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="85d93-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="85d93-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="85d93-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="85d93-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="85d93-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-152">Wartość, która wskazuje, czy włączone jest niebezpieczne udostępnianie połączenia na serwerze.</span><span class="sxs-lookup"><span data-stu-id="85d93-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="85d93-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="85d93-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="85d93-154">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="85d93-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="85d93-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="85d93-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85d93-156">Wartość, która wskazuje, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="85d93-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d93-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85d93-157">Requirements</span></span>  
  
|<span data-ttu-id="85d93-158">MOF</span><span class="sxs-lookup"><span data-stu-id="85d93-158">MOF</span></span>|<span data-ttu-id="85d93-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="85d93-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="85d93-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="85d93-160">Namespace</span></span>|<span data-ttu-id="85d93-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="85d93-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85d93-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85d93-162">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

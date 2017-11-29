---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b1542406caf9bb3684ccf2d97ed441f1dc3d0db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="81615-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="81615-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="81615-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="81615-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81615-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81615-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="81615-105">Metody</span><span class="sxs-lookup"><span data-stu-id="81615-105">Methods</span></span>  
 <span data-ttu-id="81615-106">Klasa HttpTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="81615-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81615-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="81615-107">Properties</span></span>  
 <span data-ttu-id="81615-108">Klasa HttpTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="81615-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="81615-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="81615-109">AllowCookies</span></span>  
 <span data-ttu-id="81615-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="81615-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="81615-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-112">Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="81615-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="81615-113">authenticationScheme</span><span class="sxs-lookup"><span data-stu-id="81615-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="81615-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81615-114">Data type: string</span></span>  
  
 <span data-ttu-id="81615-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-116">Schemat uwierzytelniania używany do uwierzytelniania żądań klientów przetwarzanych przez odbiornik HTTP.</span><span class="sxs-lookup"><span data-stu-id="81615-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="81615-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="81615-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="81615-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="81615-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="81615-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-120">Wartość, która wskazuje, czy serwery proxy są ignorowane w przypadku adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="81615-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="81615-121">parametru hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="81615-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="81615-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81615-122">Data type: string</span></span>  
  
 <span data-ttu-id="81615-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-124">Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="81615-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="81615-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="81615-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="81615-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="81615-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="81615-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-128">Po włączeniu połączenia HTTP są utrzymywane bez względu na poziom aktywności.</span><span class="sxs-lookup"><span data-stu-id="81615-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="81615-129">wartość maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="81615-129">MaxBufferSize</span></span>  
 <span data-ttu-id="81615-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="81615-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="81615-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-132">Maksymalny rozmiar puli buforów.</span><span class="sxs-lookup"><span data-stu-id="81615-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="81615-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="81615-133">ProxyAddress</span></span>  
 <span data-ttu-id="81615-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81615-134">Data type: string</span></span>  
  
 <span data-ttu-id="81615-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-136">Identyfikator URI zawierający adres serwera proxy do obsługi żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="81615-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="81615-137">proxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="81615-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="81615-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81615-138">Data type: string</span></span>  
  
 <span data-ttu-id="81615-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-140">Schemat uwierzytelniania używany do uwierzytelniania żądań klientów przetwarzanych przez serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="81615-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="81615-141">obszar</span><span class="sxs-lookup"><span data-stu-id="81615-141">Realm</span></span>  
 <span data-ttu-id="81615-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81615-142">Data type: string</span></span>  
  
 <span data-ttu-id="81615-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-144">Obszar uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="81615-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="81615-145">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="81615-145">TransferMode</span></span>  
 <span data-ttu-id="81615-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81615-146">Data type: string</span></span>  
  
 <span data-ttu-id="81615-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-148">Wartość określająca, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="81615-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="81615-149">unsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="81615-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="81615-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="81615-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="81615-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-152">Wartość, która wskazuje, czy na serwerze włączone jest niebezpieczne udostępnianie połączenia.</span><span class="sxs-lookup"><span data-stu-id="81615-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="81615-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="81615-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="81615-154">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="81615-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="81615-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81615-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81615-156">Wartość, która wskazuje, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="81615-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81615-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81615-157">Requirements</span></span>  
  
|<span data-ttu-id="81615-158">MOF</span><span class="sxs-lookup"><span data-stu-id="81615-158">MOF</span></span>|<span data-ttu-id="81615-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="81615-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="81615-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="81615-160">Namespace</span></span>|<span data-ttu-id="81615-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="81615-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81615-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81615-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

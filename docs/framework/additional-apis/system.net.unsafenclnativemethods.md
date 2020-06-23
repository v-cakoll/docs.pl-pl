---
title: UnsafeNclNativeMethods, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990358"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="2250c-102">UnsafeNclNativeMethods, klasa</span><span class="sxs-lookup"><span data-stu-id="2250c-102">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="2250c-103">Zawiera klasy służące do importowania niebezpiecznych metod sieci natywnych.</span><span class="sxs-lookup"><span data-stu-id="2250c-103">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="2250c-104">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="2250c-104">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="2250c-105">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2250c-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2250c-106">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="2250c-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="2250c-107">Klasa NativePKI</span><span class="sxs-lookup"><span data-stu-id="2250c-107">NativePKI class</span></span>

<span data-ttu-id="2250c-108">Zawiera metody zaimportowane z crypt32.dll.</span><span class="sxs-lookup"><span data-stu-id="2250c-108">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="2250c-109">Te metody obsługują certyfikaty przy użyciu protokołu Hypertext Transfer Protocol Secure (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="2250c-109">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="2250c-110">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="2250c-110">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="2250c-111">NativePKI. FindClientCertificates — Metoda</span><span class="sxs-lookup"><span data-stu-id="2250c-111">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="2250c-112">Odnajduje dostępne certyfikaty klienta do wysłania do serwera.</span><span class="sxs-lookup"><span data-stu-id="2250c-112">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="2250c-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2250c-113">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="2250c-114">Kolekcja dostępnych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="2250c-114">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="2250c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2250c-115">Requirements</span></span>

<span data-ttu-id="2250c-116">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="2250c-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="2250c-117">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="2250c-117">**Assembly:** System (in System.dll)</span></span>

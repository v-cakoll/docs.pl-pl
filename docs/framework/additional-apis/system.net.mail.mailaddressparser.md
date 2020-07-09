---
title: MailAddressParser, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051353"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="6e510-102">MailAddressParser, klasa</span><span class="sxs-lookup"><span data-stu-id="6e510-102">MailAddressParser class</span></span>

<span data-ttu-id="6e510-103">Analizuje adresy e-mail zgodnie z opisem w dokumencie RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="6e510-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="6e510-104">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="6e510-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="6e510-105">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6e510-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6e510-106">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="6e510-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="6e510-107">ParseAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="6e510-107">ParseAddress method</span></span>

<span data-ttu-id="6e510-108">Analizuje pojedynczy adres e-mail z określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="6e510-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="6e510-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e510-109">Parameters</span></span>

<span data-ttu-id="6e510-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6e510-110">`data` <xref:System.String></span></span>

<span data-ttu-id="6e510-111">Ciąg, który zawiera adres e-mail, który ma zostać przeanalizowany.</span><span class="sxs-lookup"><span data-stu-id="6e510-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="6e510-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6e510-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="6e510-113">Prawidłowy adres e-mail.</span><span class="sxs-lookup"><span data-stu-id="6e510-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="6e510-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="6e510-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="6e510-115">Adres e-mail jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6e510-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e510-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e510-116">Requirements</span></span>

<span data-ttu-id="6e510-117">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6e510-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6e510-118">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="6e510-118">**Assembly:** System (in System.dll)</span></span>

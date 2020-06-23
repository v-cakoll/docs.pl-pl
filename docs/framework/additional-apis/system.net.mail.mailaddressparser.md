---
title: MailAddressParser, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990385"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="61847-102">MailAddressParser, klasa</span><span class="sxs-lookup"><span data-stu-id="61847-102">MailAddressParser class</span></span>

<span data-ttu-id="61847-103">Analizuje adresy e-mail zgodnie z opisem w dokumencie RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="61847-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="61847-104">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="61847-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="61847-105">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="61847-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="61847-106">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="61847-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="61847-107">ParseAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="61847-107">ParseAddress method</span></span>

<span data-ttu-id="61847-108">Analizuje pojedynczy adres e-mail z określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="61847-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="61847-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="61847-109">Parameters</span></span>

<span data-ttu-id="61847-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="61847-110">`data` <xref:System.String></span></span>

<span data-ttu-id="61847-111">Ciąg, który zawiera adres e-mail, który ma zostać przeanalizowany.</span><span class="sxs-lookup"><span data-stu-id="61847-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="61847-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61847-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="61847-113">Prawidłowy adres e-mail.</span><span class="sxs-lookup"><span data-stu-id="61847-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="61847-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="61847-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="61847-115">Adres e-mail jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="61847-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="61847-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61847-116">Requirements</span></span>

<span data-ttu-id="61847-117">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="61847-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="61847-118">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="61847-118">**Assembly:** System (in System.dll)</span></span>

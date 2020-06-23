---
title: MailBnfHelper, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990370"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="caa49-102">MailBnfHelper, klasa</span><span class="sxs-lookup"><span data-stu-id="caa49-102">MailBnfHelper class</span></span>

<span data-ttu-id="caa49-103">Zawiera metody narzędzi do analizowania ciągów w formacie internetowym.</span><span class="sxs-lookup"><span data-stu-id="caa49-103">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="caa49-104">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="caa49-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="caa49-105">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="caa49-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="caa49-106">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="caa49-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="caa49-107">Pole Ascii7bitMaxValue</span><span class="sxs-lookup"><span data-stu-id="caa49-107">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="caa49-108">Reprezentuje maksymalną 7-bitową wartość ASCII.</span><span class="sxs-lookup"><span data-stu-id="caa49-108">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="caa49-109">Pole aText</span><span class="sxs-lookup"><span data-stu-id="caa49-109">Atext field</span></span>

<span data-ttu-id="caa49-110">Reprezentuje znaki dozwolone w atomach.</span><span class="sxs-lookup"><span data-stu-id="caa49-110">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="caa49-111">Pole CR</span><span class="sxs-lookup"><span data-stu-id="caa49-111">CR field</span></span>

<span data-ttu-id="caa49-112">Reprezentuje znak powrotu karetki.</span><span class="sxs-lookup"><span data-stu-id="caa49-112">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="caa49-113">Pole CTEXT</span><span class="sxs-lookup"><span data-stu-id="caa49-113">Ctext field</span></span>

<span data-ttu-id="caa49-114">Reprezentuje znaki dozwolone wewnątrz komentarzy.</span><span class="sxs-lookup"><span data-stu-id="caa49-114">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="caa49-115">Pole dot</span><span class="sxs-lookup"><span data-stu-id="caa49-115">Dot field</span></span>

<span data-ttu-id="caa49-116">Reprezentuje znak pełny-Stop ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="caa49-116">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="caa49-117">Pole EndComment</span><span class="sxs-lookup"><span data-stu-id="caa49-117">EndComment field</span></span>

<span data-ttu-id="caa49-118">Reprezentuje znak, który określa koniec komentarza.</span><span class="sxs-lookup"><span data-stu-id="caa49-118">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="caa49-119">Pole LF</span><span class="sxs-lookup"><span data-stu-id="caa49-119">LF field</span></span>

<span data-ttu-id="caa49-120">Reprezentuje znak wysuwu wiersza.</span><span class="sxs-lookup"><span data-stu-id="caa49-120">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="caa49-121">Pole przestrzeni</span><span class="sxs-lookup"><span data-stu-id="caa49-121">Space field</span></span>

<span data-ttu-id="caa49-122">Reprezentuje znak spacji.</span><span class="sxs-lookup"><span data-stu-id="caa49-122">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="caa49-123">Pole StartComment</span><span class="sxs-lookup"><span data-stu-id="caa49-123">StartComment field</span></span>

<span data-ttu-id="caa49-124">Reprezentuje znak określający początek komentarza.</span><span class="sxs-lookup"><span data-stu-id="caa49-124">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="caa49-125">Pole tabulacji</span><span class="sxs-lookup"><span data-stu-id="caa49-125">Tab field</span></span>

<span data-ttu-id="caa49-126">Reprezentuje znak tabulacji.</span><span class="sxs-lookup"><span data-stu-id="caa49-126">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="caa49-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="caa49-127">Requirements</span></span>

<span data-ttu-id="caa49-128">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="caa49-128">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="caa49-129">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="caa49-129">**Assembly:** System (in System.dll)</span></span>

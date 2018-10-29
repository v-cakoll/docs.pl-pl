---
title: Wytyczne dotyczące użycia
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e583bf7768c60477effb6c1cf9b838ae4c8c182
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197941"
---
# <a name="usage-guidelines"></a><span data-ttu-id="521bb-102">Wytyczne dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="521bb-102">Usage guidelines</span></span>

<span data-ttu-id="521bb-103">Ta sekcja zawiera wskazówki dotyczące korzystania z popularnych typów w publicznie dostępne interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="521bb-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="521bb-104">Dotyczy on bezpośredniego użycia wbudowanych typów Framework (np. serializacji atrybutów) i przeciążanie operatorów wspólnej.</span><span class="sxs-lookup"><span data-stu-id="521bb-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="521bb-105"><xref:System.IDisposable?displayProperty=nameWithType> Interfejsu nie została uwzględniona w tej sekcji, ale została omówiona w [wzorzec Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="521bb-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="521bb-106">Wytyczne i dodatkowe informacje na temat innych typowych wbudowanych typów programu .NET Framework, zobacz Tematy referencyjne dla następujących: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="521bb-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="521bb-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="521bb-107">In this section</span></span>

[<span data-ttu-id="521bb-108">Tablice</span><span class="sxs-lookup"><span data-stu-id="521bb-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="521bb-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="521bb-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="521bb-110">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="521bb-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="521bb-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="521bb-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="521bb-112">Używanie zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="521bb-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="521bb-113">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="521bb-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="521bb-114">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="521bb-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="521bb-115">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="521bb-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="521bb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="521bb-116">See also</span></span>

- [<span data-ttu-id="521bb-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="521bb-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

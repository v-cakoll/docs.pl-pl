---
title: Wytyczne dotyczące użycia
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 57f6600f60e99c72b72c9f82856dc9eb631a9d4b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709000"
---
# <a name="usage-guidelines"></a><span data-ttu-id="bfbf7-102">Wytyczne dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="bfbf7-102">Usage guidelines</span></span>

<span data-ttu-id="bfbf7-103">Ta sekcja zawiera wskazówki dotyczące używania typów wspólnych w publicznie dostępnych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="bfbf7-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="bfbf7-104">Zajmuje się bezpośrednim użyciem wbudowanych typów struktur (np. atrybutów serializacji) i przeciążania typowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="bfbf7-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="bfbf7-105">Interfejs <xref:System.IDisposable?displayProperty=nameWithType> nie został uwzględniony w tej sekcji, ale został omówiony w sekcji "Usuwanie [wzorców](../garbage-collection/implementing-dispose.md) ".</span><span class="sxs-lookup"><span data-stu-id="bfbf7-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="bfbf7-106">Aby uzyskać wytyczne i dodatkowe informacje na temat innych typowych, wbudowanych typów .NET Framework, zobacz tematy referencyjne dotyczące następujących zagadnień: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfbf7-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bfbf7-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bfbf7-107">In this section</span></span>

[<span data-ttu-id="bfbf7-108">Tablice</span><span class="sxs-lookup"><span data-stu-id="bfbf7-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="bfbf7-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bfbf7-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="bfbf7-110">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="bfbf7-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="bfbf7-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="bfbf7-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="bfbf7-112">Używanie zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="bfbf7-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="bfbf7-113">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="bfbf7-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="bfbf7-114">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="bfbf7-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="bfbf7-115">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="bfbf7-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bfbf7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfbf7-116">See also</span></span>

- [<span data-ttu-id="bfbf7-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="bfbf7-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

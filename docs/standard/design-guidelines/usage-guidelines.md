---
title: Zalecenia dotyczące użycia
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 03eaba3e52cb25619f65637efb4f414c22770440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291347"
---
# <a name="usage-guidelines"></a><span data-ttu-id="7126c-102">Zalecenia dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="7126c-102">Usage guidelines</span></span>

<span data-ttu-id="7126c-103">Ta sekcja zawiera wskazówki dotyczące używania typów wspólnych w publicznie dostępnych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="7126c-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="7126c-104">Zajmuje się bezpośrednim użyciem wbudowanych typów struktur (np. atrybutów serializacji) i przeciążania typowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="7126c-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="7126c-105"><xref:System.IDisposable?displayProperty=nameWithType>Interfejs nie został uwzględniony w tej sekcji, ale został omówiony w sekcji "Usuwanie [wzorców](../garbage-collection/implementing-dispose.md) ".</span><span class="sxs-lookup"><span data-stu-id="7126c-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="7126c-106">Aby uzyskać wytyczne i dodatkowe informacje na temat innych typowych, wbudowanych typów .NET Framework, zobacz tematy referencyjne dotyczące następujących zagadnień:,,,,,, <xref:System.DateTime?displayProperty=nameWithType> <xref:System.DateTimeOffset?displayProperty=nameWithType> <xref:System.ICloneable?displayProperty=nameWithType> <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7126c-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7126c-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7126c-107">In this section</span></span>

[<span data-ttu-id="7126c-108">Tablice</span><span class="sxs-lookup"><span data-stu-id="7126c-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="7126c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7126c-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="7126c-110">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="7126c-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="7126c-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="7126c-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="7126c-112">Użycie metody System. XML</span><span class="sxs-lookup"><span data-stu-id="7126c-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="7126c-113">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="7126c-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="7126c-114">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="7126c-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="7126c-115">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="7126c-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7126c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7126c-116">See also</span></span>

- [<span data-ttu-id="7126c-117">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="7126c-117">Framework Design Guidelines</span></span>](index.md)

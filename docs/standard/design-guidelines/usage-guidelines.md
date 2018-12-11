---
title: Wytyczne dotyczące użycia
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 761570b899a2a36391eb81dc7f42e13fff1f14ef
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155408"
---
# <a name="usage-guidelines"></a><span data-ttu-id="42725-102">Wytyczne dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="42725-102">Usage guidelines</span></span>

<span data-ttu-id="42725-103">Ta sekcja zawiera wskazówki dotyczące korzystania z popularnych typów w publicznie dostępne interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="42725-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="42725-104">Dotyczy on bezpośredniego użycia wbudowanych typów Framework (np. serializacji atrybutów) i przeciążanie operatorów wspólnej.</span><span class="sxs-lookup"><span data-stu-id="42725-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="42725-105"><xref:System.IDisposable?displayProperty=nameWithType> Interfejsu nie została uwzględniona w tej sekcji, ale została omówiona w [wzorzec Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="42725-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="42725-106">Wytyczne i dodatkowe informacje na temat innych typowych wbudowanych typów programu .NET Framework, zobacz Tematy referencyjne dla następujących: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42725-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="42725-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="42725-107">In this section</span></span>

[<span data-ttu-id="42725-108">Tablice</span><span class="sxs-lookup"><span data-stu-id="42725-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="42725-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="42725-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="42725-110">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="42725-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="42725-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="42725-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="42725-112">Używanie zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="42725-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="42725-113">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="42725-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="42725-114">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="42725-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="42725-115">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="42725-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="42725-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42725-116">See also</span></span>

- [<span data-ttu-id="42725-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="42725-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

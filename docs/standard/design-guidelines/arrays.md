---
title: Tablice
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741808"
---
# <a name="arrays"></a><span data-ttu-id="ca492-102">Tablice</span><span class="sxs-lookup"><span data-stu-id="ca492-102">Arrays</span></span>
<span data-ttu-id="ca492-103">✔️ Preferuj przy użyciu kolekcji za pośrednictwem tablic w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="ca492-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="ca492-104">Sekcja [kolekcje](../../../docs/standard/design-guidelines/guidelines-for-collections.md) zawiera szczegółowe informacje dotyczące wyboru między kolekcjami i tablicami.</span><span class="sxs-lookup"><span data-stu-id="ca492-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="ca492-105">❌ nie używaj pól tablicy tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ca492-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="ca492-106">Samo pole jest tylko do odczytu i nie można go zmienić, ale elementy w tablicy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="ca492-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="ca492-107">✔️ ROZWAŻYĆ użycie tablic nieregularnych zamiast tablic wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="ca492-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="ca492-108">Tablica nieregularna jest tablicą zawierającą elementy, które są również tablicami.</span><span class="sxs-lookup"><span data-stu-id="ca492-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="ca492-109">Tablice wchodzące w skład elementów mogą mieć różne rozmiary, co prowadzi do mniejszej ilości wolnego miejsca dla niektórych zestawów danych (np. macierzy rozrzedzonych) w porównaniu do tablic wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="ca492-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="ca492-110">Ponadto środowisko CLR optymalizuje operacje indeksowania w tablicach nieregularnych, dzięki czemu mogą one mieć lepszą wydajność środowiska uruchomieniowego w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="ca492-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="ca492-111">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="ca492-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ca492-112">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="ca492-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ca492-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca492-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="ca492-114">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ca492-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ca492-115">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="ca492-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

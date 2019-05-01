---
title: Tablice
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: KrzysztofCwalina
ms.openlocfilehash: dd30cdee0440553a9f955f0b3f4ee420e938b9ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864120"
---
# <a name="arrays"></a><span data-ttu-id="b425a-102">Tablice</span><span class="sxs-lookup"><span data-stu-id="b425a-102">Arrays</span></span>
<span data-ttu-id="b425a-103">**✓ DO** preferowane przy użyciu kolekcji za pośrednictwem tablic w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="b425a-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="b425a-104">[Kolekcje](../../../docs/standard/design-guidelines/guidelines-for-collections.md) sekcja zawiera szczegółowe informacje o tym, jak dokonać wyboru między kolekcje i tablice.</span><span class="sxs-lookup"><span data-stu-id="b425a-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="b425a-105">**X DO NOT** użyć pola tablicy tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b425a-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="b425a-106">Samo pole jest tylko do odczytu i nie można zmienić, ale można zmienić elementy w tablicy.</span><span class="sxs-lookup"><span data-stu-id="b425a-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="b425a-107">**✓ CONSIDER** za pomocą Tablice nieregularne zamiast wielowymiarowych tablic.</span><span class="sxs-lookup"><span data-stu-id="b425a-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="b425a-108">Nieregularna tablica jest tablicy o liczbie elementów, które również są tablicami.</span><span class="sxs-lookup"><span data-stu-id="b425a-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="b425a-109">Tablice, które tworzą elementy mogą być różne rozmiary, co zapewnia większą oszczędność miejsca dla niektórych zestawów danych (np. macierz rozrzedzone) w porównaniu do tablic wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="b425a-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="b425a-110">Ponadto środowisko CLR optymalizuje operacje indeksowania w Tablice nieregularne tak może charakteryzują się lepszą wydajność środowiska uruchomieniowego w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="b425a-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="b425a-111">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="b425a-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b425a-112">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="b425a-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b425a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b425a-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="b425a-114">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="b425a-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b425a-115">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="b425a-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

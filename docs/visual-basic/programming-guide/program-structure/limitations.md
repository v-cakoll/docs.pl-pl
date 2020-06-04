---
title: Ograniczenia
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 46294b68bda8a5d2d21c0e4efea6a78e6a265ffe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403190"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="8ce92-102">Ograniczenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ce92-102">Visual Basic Limitations</span></span>
<span data-ttu-id="8ce92-103">Wcześniejsze wersje Visual Basic wymuszają granice w kodzie, takie jak długość nazw zmiennych, liczba zmiennych dozwolona w modułach i rozmiar modułu.</span><span class="sxs-lookup"><span data-stu-id="8ce92-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="8ce92-104">W Visual Basic .NET te ograniczenia były swobodne, co zapewnia większą swobodę pisania i rozmieszczania kodu.</span><span class="sxs-lookup"><span data-stu-id="8ce92-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="8ce92-105">Limity fizyczne są zależne od większej ilości pamięci w czasie wykonywania niż kwestie dotyczące czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8ce92-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="8ce92-106">W przypadku korzystania z rozsądnych praktyk programistycznych i dzielenia dużych aplikacji na wiele klas i modułów, istnieje bardzo mało znaczące prawdopodobieństwo napotkania wewnętrznego ograniczenia Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8ce92-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="8ce92-107">Poniżej przedstawiono niektóre ograniczenia, które mogą wystąpić w skrajnych przypadkach:</span><span class="sxs-lookup"><span data-stu-id="8ce92-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="8ce92-108">**Długość nazwy.**</span><span class="sxs-lookup"><span data-stu-id="8ce92-108">**Name Length.**</span></span> <span data-ttu-id="8ce92-109">Nazwa każdego zadeklarowanego elementu programowania zawiera maksymalną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="8ce92-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="8ce92-110">Ta wartość maksymalna ma zastosowanie do całego ciągu kwalifikacji, jeśli nazwa elementu jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="8ce92-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="8ce92-111">Zobacz [zadeklarowane nazwy elementów](../language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="8ce92-111">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="8ce92-112">**Długość wiersza.**</span><span class="sxs-lookup"><span data-stu-id="8ce92-112">**Line Length.**</span></span> <span data-ttu-id="8ce92-113">W fizycznym wierszu kodu źródłowego istnieje maksymalnie 65535 znaków.</span><span class="sxs-lookup"><span data-stu-id="8ce92-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="8ce92-114">Logiczny wiersz kodu źródłowego może być dłuższy w przypadku używania znaków kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="8ce92-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="8ce92-115">Zobacz [jak: przerywanie i łączenie instrukcji w kodzie](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="8ce92-115">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="8ce92-116">**Wymiary tablicy.**</span><span class="sxs-lookup"><span data-stu-id="8ce92-116">**Array Dimensions.**</span></span> <span data-ttu-id="8ce92-117">Istnieje maksymalna liczba wymiarów, które można zadeklarować dla tablicy.</span><span class="sxs-lookup"><span data-stu-id="8ce92-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="8ce92-118">Ogranicza to liczbę indeksów, których można użyć do określenia elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="8ce92-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="8ce92-119">Zobacz [Wymiary tablicy w Visual Basic](../language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="8ce92-119">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="8ce92-120">**Długość ciągu.**</span><span class="sxs-lookup"><span data-stu-id="8ce92-120">**String Length.**</span></span> <span data-ttu-id="8ce92-121">Istnieje maksymalna liczba znaków Unicode, które można przechowywać w jednym ciągu.</span><span class="sxs-lookup"><span data-stu-id="8ce92-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="8ce92-122">Zobacz [Typ danych ciągu](../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="8ce92-122">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="8ce92-123">**Długość ciągu środowiska.**</span><span class="sxs-lookup"><span data-stu-id="8ce92-123">**Environment String Length.**</span></span> <span data-ttu-id="8ce92-124">Dla każdego ciągu środowiska, który jest używany jako argument wiersza polecenia, istnieje maksymalnie 32768 znaków.</span><span class="sxs-lookup"><span data-stu-id="8ce92-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="8ce92-125">Jest to ograniczenie na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="8ce92-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce92-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ce92-126">See also</span></span>

- [<span data-ttu-id="8ce92-127">Struktura programu i konwencje związane z kodem</span><span class="sxs-lookup"><span data-stu-id="8ce92-127">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="8ce92-128">Visual Basic — Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="8ce92-128">Visual Basic Naming Conventions</span></span>](naming-conventions.md)

---
title: Niebezpieczny kod i wskaźniki C# — Przewodnik programistyczny
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711834"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="78a3f-102">Niebezpieczny kod i wskaźnikiC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="78a3f-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="78a3f-103">Aby zachować bezpieczeństwo typów i zabezpieczenia, C# program nie obsługuje domyślnie arytmetycznego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="78a3f-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="78a3f-104">Jednak za pomocą słowa kluczowego [UNSAFE](../../language-reference/keywords/unsafe.md) można zdefiniować niebezpieczny kontekst, w którym można używać wskaźników.</span><span class="sxs-lookup"><span data-stu-id="78a3f-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="78a3f-105">Aby uzyskać więcej informacji na temat wskaźników, zobacz [typy wskaźnika](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="78a3f-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78a3f-106">W środowisku uruchomieniowym języka wspólnego (CLR) kod niebezpieczny jest określany jako kod niemożliwy do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="78a3f-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="78a3f-107">Kod niebezpieczny C# w programie nie musi być niebezpieczny; jest to tylko kod, którego bezpieczeństwo nie może być zweryfikowane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="78a3f-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="78a3f-108">W związku z tym środowisko CLR wykona tylko niebezpieczny kod, jeśli znajduje się w w pełni zaufanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="78a3f-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="78a3f-109">Jeśli używasz niebezpiecznego kodu, jest odpowiedzialny za upewnienie się, że Twój kod nie wprowadza zagrożeń bezpieczeństwa lub błędy wskaźników.</span><span class="sxs-lookup"><span data-stu-id="78a3f-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="78a3f-110">Przegląd niebezpiecznego kodu</span><span class="sxs-lookup"><span data-stu-id="78a3f-110">Unsafe code overview</span></span>

<span data-ttu-id="78a3f-111">Kod niebezpieczny ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="78a3f-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="78a3f-112">Metody, typy i bloki kodu można definiować jako niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="78a3f-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="78a3f-113">W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji przez usunięcie kontroli granic tablicy.</span><span class="sxs-lookup"><span data-stu-id="78a3f-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="78a3f-114">Kod niebezpieczny jest wymagany po wywołaniu funkcji natywnych, które wymagają wskaźników.</span><span class="sxs-lookup"><span data-stu-id="78a3f-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="78a3f-115">Użycie niebezpiecznego kodu wprowadza zagrożenia bezpieczeństwa i stabilności.</span><span class="sxs-lookup"><span data-stu-id="78a3f-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="78a3f-116">Kod, który zawiera niebezpieczne bloki, musi być skompilowany przy użyciu opcji [niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="78a3f-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="78a3f-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="78a3f-117">Related sections</span></span>

<span data-ttu-id="78a3f-118">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="78a3f-118">For more information, see:</span></span>

- [<span data-ttu-id="78a3f-119">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="78a3f-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="78a3f-120">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="78a3f-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="78a3f-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="78a3f-121">C# language specification</span></span>

<span data-ttu-id="78a3f-122">Aby uzyskać więcej informacji, zobacz temat dotyczący [niebezpiecznego kodu](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="78a3f-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="78a3f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78a3f-123">See also</span></span>

- [<span data-ttu-id="78a3f-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="78a3f-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="78a3f-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="78a3f-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)

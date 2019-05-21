---
title: Niebezpieczny kod i wskaźniki - C# Programming Guide
ms.custom: seodec18
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
ms.openlocfilehash: 99f0b925a37bff8b6ab1ff46e9ce2f0ea0a38aed
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959480"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="0cbf6-102">Niebezpieczny kod i wskaźniki (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="0cbf6-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="0cbf6-103">Aby zachować bezpieczeństwo typów i zabezpieczeń, C# nie obsługuje arytmetyki wskaźnika domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="0cbf6-104">Jednak przy użyciu [niebezpieczne](../../language-reference/keywords/unsafe.md) słów kluczowych, można zdefiniować niebezpieczny kontekst, w którym można użyć wskaźników.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="0cbf6-105">Aby uzyskać więcej informacji o wskaźnikach, zobacz [typy wskaźników](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="0cbf6-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cbf6-106">W środowisko uruchomieniowe języka wspólnego (CLR) niebezpieczny kod nazywa się zweryfikowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="0cbf6-107">Niebezpieczny kod w języku C# nie są zawsze niebezpieczne; jest po prostu kod bezpieczeństwa, którego nie można zweryfikować przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="0cbf6-108">Środowisko CLR w związku z tym tylko wykona niebezpieczny kod jeśli znajduje się w zestawie całkowicie zaufanym.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="0cbf6-109">Jeśli używasz niebezpieczny kod, jest odpowiedzialny za zapewnienie, kod nie wprowadzają zagrożenia dla bezpieczeństwa lub wskaźnik błędów.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="0cbf6-110">Niebezpieczne Przegląd kodu</span><span class="sxs-lookup"><span data-stu-id="0cbf6-110">Unsafe code overview</span></span>

<span data-ttu-id="0cbf6-111">Niebezpieczny kod ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="0cbf6-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="0cbf6-112">Metody, typy i bloków kodu mogą być definiowane jako niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="0cbf6-113">W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji, usuwając kontroli granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="0cbf6-114">Niebezpieczny kod jest wymagany podczas wywoływania funkcji natywnych, które wymagają wskaźników.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="0cbf6-115">Za pomocą niebezpieczny kod wprowadza zagrożenia bezpieczeństwa i stabilności.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="0cbf6-116">Kod, który zawiera bloki niebezpieczne musi być skompilowana przy użyciu [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="0cbf6-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="0cbf6-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0cbf6-117">Related sections</span></span>

<span data-ttu-id="0cbf6-118">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="0cbf6-118">For more information, see:</span></span>

- [<span data-ttu-id="0cbf6-119">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="0cbf6-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="0cbf6-120">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="0cbf6-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="0cbf6-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0cbf6-121">C# language specification</span></span>

<span data-ttu-id="0cbf6-122">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) tematu [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0cbf6-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0cbf6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cbf6-123">See also</span></span>

- [<span data-ttu-id="0cbf6-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0cbf6-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0cbf6-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="0cbf6-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)

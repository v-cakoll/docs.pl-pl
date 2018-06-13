---
title: 'Porady: inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 1f5f068cd8dc3787eb8cb2cd72cc30e9ea159390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320911"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="49dd1-102">Porady: inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="49dd1-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="49dd1-103">Inicjatory obiektów służy do zainicjowania obiekty typu w sposób deklaratywne bez jawnego wywołania konstruktora dla typu.</span><span class="sxs-lookup"><span data-stu-id="49dd1-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="49dd1-104">Poniższe przykłady przedstawiają sposób inicjatory obiektów za pomocą nazwane obiekty.</span><span class="sxs-lookup"><span data-stu-id="49dd1-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="49dd1-105">Procesy kompilatora obiekt inicjatory pierwszy uzyskiwanie dostępu do domyślnego konstruktora wystąpienia, a następnie przetwarzania operacji inicjowania elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="49dd1-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="49dd1-106">W związku z tym jeśli domyślny konstruktor jest zadeklarowany jako `private` w klasie, inicjatory obiektów, które wymagają dostępu publicznego zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="49dd1-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="49dd1-107">Jeśli definiujesz typu anonimowego, należy użyć inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="49dd1-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="49dd1-108">Aby uzyskać więcej informacji, zobacz [porady: zwraca podzestawy elementu właściwości w zapytaniu](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="49dd1-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49dd1-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="49dd1-109">Example</span></span>  
 <span data-ttu-id="49dd1-110">Poniższy przykład pokazuje, jak zainicjować nowe `StudentName` typu przy użyciu inicjatory obiektów.</span><span class="sxs-lookup"><span data-stu-id="49dd1-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="49dd1-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="49dd1-111">Example</span></span>  
 <span data-ttu-id="49dd1-112">Poniższy przykład pokazuje, jak zainicjować to zbiór `StudentName` typów za pomocą inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49dd1-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="49dd1-113">Należy pamiętać, że inicjatora kolekcji serii inicjatory obiektów rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="49dd1-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49dd1-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="49dd1-114">Compiling the Code</span></span>  
 <span data-ttu-id="49dd1-115">Aby uruchomić ten kod, skopiuj i Wklej klasy w projektach Visual C# console aplikacji utworzony w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49dd1-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49dd1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49dd1-116">See Also</span></span>  
 [<span data-ttu-id="49dd1-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="49dd1-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="49dd1-118">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="49dd1-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

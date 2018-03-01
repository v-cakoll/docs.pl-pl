---
title: "Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="f54a4-102">Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego</span><span class="sxs-lookup"><span data-stu-id="f54a4-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="f54a4-103">Używa instrukcji przypisania `AddressOf` można przypisać adres ogólnego procedury delegata, ale nie dostarcza żadnych argumentów typu ogólnego procedury.</span><span class="sxs-lookup"><span data-stu-id="f54a4-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="f54a4-104">Zwykle po wywołaniu typu ogólnego, należy podać typ argumentu dla każdego parametru typu, który definiuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="f54a4-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="f54a4-105">Jeśli nie podasz żadnych argumentów typu, kompilator próbuje wnioskowanie typów, które mają być przekazane do parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="f54a4-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="f54a4-106">Jeśli kontekst nie zawiera wystarczających informacji dla kompilatora w celu uwzględnienia typów, generowany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="f54a4-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="f54a4-107">**Identyfikator błędu:** BC36564</span><span class="sxs-lookup"><span data-stu-id="f54a4-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f54a4-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f54a4-108">To correct this error</span></span>  
  
-   <span data-ttu-id="f54a4-109">Określ argumenty typu ogólnego procedurą w `AddressOf` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f54a4-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f54a4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f54a4-110">See Also</span></span>  
 [<span data-ttu-id="f54a4-111">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f54a4-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="f54a4-112">AddressOf — Operator</span><span class="sxs-lookup"><span data-stu-id="f54a4-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="f54a4-113">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f54a4-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="f54a4-114">Lista typów</span><span class="sxs-lookup"><span data-stu-id="f54a4-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="f54a4-115">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="f54a4-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

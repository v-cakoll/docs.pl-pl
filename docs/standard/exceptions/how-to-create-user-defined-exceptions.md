---
title: 'Porady: tworzenie wyjątków zdefiniowanych przez użytkownika'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90bf9d6dbfebf8f7c1aa22e5844cf4e30b89b8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572804"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="1c262-102">Tworzenie wyjątków zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1c262-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="1c262-103">.NET dostarcza hierarchię klas wyjątków wywodzących się z klasy podstawowej <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="1c262-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="1c262-104">Jeśli żaden z wstępnie zdefiniowanych wyjątków nie spełnia Twoich potrzeb, możesz utworzyć własne klasy wyjątków wywodzące się z klasy <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="1c262-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="1c262-105">Tworząc własne wyjątki, zakończ nazwę klasy zdefiniowanego przez siebie wyjątku słowem „Exception” i utwórz trzy wspólne konstruktory, jak pokazano w przykładzie poniżej. </span><span class="sxs-lookup"><span data-stu-id="1c262-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception," and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="1c262-106">W przykładzie zdefiniowano klasę wyjątku o nazwie `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="1c262-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="1c262-107">Klasa pochodzi od <xref:System.Exception> i zawiera trzy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1c262-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="1c262-108">Jeśli używasz komunikacji zdalnej, upewnij się, że metadane zdefiniowane przez użytkownika wyjątków są dostępne na serwerze (strona wywoływana) i dla klienta (obiekt serwera proxy lub strona wywołująca).</span><span class="sxs-lookup"><span data-stu-id="1c262-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="1c262-109">Aby dowiedzieć się więcej, zobacz [Najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="1c262-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c262-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c262-110">See Also</span></span>  
[<span data-ttu-id="1c262-111">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="1c262-111">Exceptions</span></span>](index.md)

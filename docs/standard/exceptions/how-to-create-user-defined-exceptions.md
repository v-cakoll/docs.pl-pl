---
title: 'Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika'
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
ms.openlocfilehash: 42860f549877436f43bfdc20fb3abde91d36101d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783189"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="4c1d2-102">Jak utworzyć wyjątki zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="4c1d2-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="4c1d2-103">.NET dostarcza hierarchię klas wyjątków wywodzących się z klasy podstawowej <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="4c1d2-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="4c1d2-104">Jeśli żaden z wstępnie zdefiniowanych wyjątków nie spełnia Twoich potrzeb, możesz utworzyć własne klasy wyjątków wywodzące się z klasy <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="4c1d2-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="4c1d2-105">Podczas tworzenia własnych wyjątków, zakończenia Nazwa klasy wyjątków zdefiniowanych przez użytkownika z wyrazem "Wyjątek", a następnie wdrożyć trzech typowych konstruktorów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4c1d2-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="4c1d2-106">W przykładzie zdefiniowano klasę wyjątku o nazwie `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="4c1d2-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="4c1d2-107">Klasa jest pochodną <xref:System.Exception> i zawiera trzy konstruktory.</span><span class="sxs-lookup"><span data-stu-id="4c1d2-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="4c1d2-108">Jeśli używasz komunikacji zdalnej, upewnij się, że metadane zdefiniowane przez użytkownika wyjątków są dostępne na serwerze (strona wywoływana) i dla klienta (obiekt serwera proxy lub strona wywołująca).</span><span class="sxs-lookup"><span data-stu-id="4c1d2-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="4c1d2-109">Aby dowiedzieć się więcej, zobacz [Najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="4c1d2-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c1d2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c1d2-110">See also</span></span>

- [<span data-ttu-id="4c1d2-111">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="4c1d2-111">Exceptions</span></span>](index.md)

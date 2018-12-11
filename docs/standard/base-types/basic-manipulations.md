---
title: 'Instrukcje: Wykonywanie podstawowych działań na ciągach w .NET'
description: Zobacz przykład, który wywołuje wiele metod ciągów.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11f8043745c631a642b437339240cbf06fc8df5b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130640"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="1ee91-103">Instrukcje: Wykonywanie podstawowych działań na ciągach w .NET</span><span class="sxs-lookup"><span data-stu-id="1ee91-103">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="1ee91-104">W poniższym przykładzie użyto niektórych metod omówione w [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) tematy, aby utworzyć klasę, która wykonuje działań na ciągach w taki sposób, który można znaleźć w rzeczywistych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="1ee91-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="1ee91-105">`MailToData` Klasa przechowuje nazwę i adres osoba w oddzielnych właściwości i zapewnia sposób łączenia `City`, `State`, i `Zip` pól w jeden ciąg do wyświetlania użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="1ee91-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="1ee91-106">Ponadto klasa pozwala użytkownikowi wprowadzanie miejscowość, stan i kod POCZTOWY jako pojedynczy ciąg; Aplikacja automatycznie analizuje jeden ciąg i wprowadza odpowiednie informacje w odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ee91-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="1ee91-107">Dla uproszczenia w tym przykładzie użyto aplikacji konsoli przy użyciu interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1ee91-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ee91-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ee91-108">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="1ee91-109">Jeśli poprzedni kod jest wykonywany, użytkownik jest proszony o wprowadzenie swojej nazwy i adresu.</span><span class="sxs-lookup"><span data-stu-id="1ee91-109">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="1ee91-110">Aplikacja umieszcza informacje w odpowiednie właściwości i wyświetla informacje użytkownika, tworząc jeden ciąg, który wyświetla miejscowość, stan i kod POCZTOWY.</span><span class="sxs-lookup"><span data-stu-id="1ee91-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee91-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ee91-111">See also</span></span>

- [<span data-ttu-id="1ee91-112">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="1ee91-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

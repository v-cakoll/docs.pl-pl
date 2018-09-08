---
title: 'Porady: wykonywanie podstawowych działań na ciągach w programie .NET Framework'
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
ms.openlocfilehash: 1206648c694c9f09a600e3c70f4aa27118b2d458
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178055"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="92576-102">Porady: wykonywanie podstawowych działań na ciągach w .NET</span><span class="sxs-lookup"><span data-stu-id="92576-102">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="92576-103">W poniższym przykładzie użyto niektórych metod omówione w [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) tematy, aby utworzyć klasę, która wykonuje działań na ciągach w taki sposób, który można znaleźć w rzeczywistych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="92576-103">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="92576-104">`MailToData` Klasa przechowuje nazwę i adres osoba w oddzielnych właściwości i zapewnia sposób łączenia `City`, `State`, i `Zip` pól w jeden ciąg do wyświetlania użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="92576-104">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="92576-105">Ponadto klasa pozwala użytkownikowi wprowadzanie miejscowość, stan i kod POCZTOWY jako pojedynczy ciąg; Aplikacja automatycznie analizuje jeden ciąg i wprowadza odpowiednie informacje w odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="92576-105">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="92576-106">Dla uproszczenia w tym przykładzie użyto aplikacji konsoli przy użyciu interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="92576-106">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92576-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="92576-107">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="92576-108">Jeśli poprzedni kod jest wykonywany, użytkownik jest proszony o wprowadzenie swojej nazwy i adresu.</span><span class="sxs-lookup"><span data-stu-id="92576-108">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="92576-109">Aplikacja umieszcza informacje w odpowiednie właściwości i wyświetla informacje użytkownika, tworząc jeden ciąg, który wyświetla miejscowość, stan i kod POCZTOWY.</span><span class="sxs-lookup"><span data-stu-id="92576-109">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92576-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92576-110">See also</span></span>

- [<span data-ttu-id="92576-111">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="92576-111">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

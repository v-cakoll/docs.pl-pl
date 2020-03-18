---
title: Podstawowe manipulacje ciągami w .NET
description: Zobacz przykład, który wywołuje wiele metod ciągu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 87ce7a79ce18ca8f5579841ad9e52e2519d6ac73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187259"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="2dc6a-103">Jak: Wykonywanie podstawowych manipulacji ciągami w .NET</span><span class="sxs-lookup"><span data-stu-id="2dc6a-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="2dc6a-104">W poniższym przykładzie użyto niektórych metod omówione w [podstawowych operacji ciągów](../../../docs/standard/base-types/basic-string-operations.md) tematy do konstruowania klasy, która wykonuje manipulacje ciągami w sposób, który można znaleźć w aplikacji w świecie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="2dc6a-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="2dc6a-105">Klasa `MailToData` przechowuje nazwę i adres osoby w oddzielnych właściwościach i `City` `State`umożliwia `Zip` połączenie , i pola w jeden ciąg do wyświetlenia dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2dc6a-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="2dc6a-106">Ponadto klasa umożliwia użytkownikowi wprowadzenie informacji o mieście, stanie i kodzie pocztowym jako pojedynczy ciąg; aplikacja automatycznie analizuje pojedynczy ciąg i wprowadza odpowiednie informacje do odpowiedniej właściwości.</span><span class="sxs-lookup"><span data-stu-id="2dc6a-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="2dc6a-107">Dla uproszczenia w tym przykładzie używa aplikacji konsoli z interfejsem wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2dc6a-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dc6a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2dc6a-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="2dc6a-109">Po wykonaniu poprzedniego kodu użytkownik jest proszony o podanie nazwy i adresu.</span><span class="sxs-lookup"><span data-stu-id="2dc6a-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="2dc6a-110">Aplikacja umieszcza informacje w odpowiednich właściwościach i wyświetla informacje z powrotem do użytkownika, tworząc pojedynczy ciąg, który wyświetla informacje o mieście, stanie i kodzie pocztowym.</span><span class="sxs-lookup"><span data-stu-id="2dc6a-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc6a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2dc6a-111">See also</span></span>

- [<span data-ttu-id="2dc6a-112">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="2dc6a-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

---
title: "Porady: wykonywanie podstawowych działań na ciągach w programie .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8d3d5351a0a639a3f0b674640bcaaf7321ca0d76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="d8fdf-102">Porady: wykonywanie podstawowych działań na ciągach w .NET</span><span class="sxs-lookup"><span data-stu-id="d8fdf-102">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="d8fdf-103">W poniższym przykładzie użyto niektóre metody omówione w [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) tematy, aby utworzyć klasę, która wykonuje na ciągach w sposób, który może zostać znaleziony w rzeczywistych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d8fdf-103">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="d8fdf-104">`MailToData` Klasy przechowuje nazwę i adres osoby w oddzielnych właściwości i umożliwia łączenie `City`, `State`, i `Zip` pól w jednym ciągu do wyświetlenia dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d8fdf-104">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="d8fdf-105">Ponadto klasa umożliwia użytkownikowi Wprowadź miejscowość, stan i kod POCZTOWY jako pojedynczy ciąg; Aplikacja automatycznie analizuje jeden ciąg i wprowadza odpowiednie informacje do odpowiadających im właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8fdf-105">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="d8fdf-106">Dla uproszczenia w tym przykładzie użyto aplikacji konsoli przy użyciu interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d8fdf-106">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8fdf-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8fdf-107">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="d8fdf-108">Jeśli poprzedni kod jest wykonywane, użytkownik jest proszony o wprowadzenie jego nazwę lub adres.</span><span class="sxs-lookup"><span data-stu-id="d8fdf-108">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="d8fdf-109">Aplikacja umieszcza informacje w odpowiednich właściwości i wyświetla informacje do użytkownika, tworzenie jeden ciąg, który wyświetla miejscowość, stan i kod POCZTOWY.</span><span class="sxs-lookup"><span data-stu-id="d8fdf-109">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fdf-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8fdf-110">See Also</span></span>  
 [<span data-ttu-id="d8fdf-111">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="d8fdf-111">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

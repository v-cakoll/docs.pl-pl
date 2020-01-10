---
title: 'Instrukcje: wykonywanie podstawowych operacji na ciągach w programie .NET'
description: Zobacz przykład, który wywołuje wiele metod String.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: ff7abee460b4085fa9e039e678c975338ccb511a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711509"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="c2cc6-103">Instrukcje: wykonywanie podstawowych operacji na ciągach w programie .NET</span><span class="sxs-lookup"><span data-stu-id="c2cc6-103">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="c2cc6-104">W poniższym przykładzie zastosowano niektóre metody omówione w temacie [podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md) w celu skonstruowania klasy służącej do manipulowania ciągami w sposób, który może znajdować się w rzeczywistej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2cc6-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="c2cc6-105">Klasa `MailToData` przechowuje nazwę i adres osoby w osobnych właściwościach i zapewnia sposób łączenia pól `City`, `State`i `Zip` w jeden ciąg do wyświetlania użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="c2cc6-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="c2cc6-106">Ponadto Klasa umożliwia użytkownikowi wprowadzanie informacji o miejscowości, stanie i kodzie POCZTOWYm jako jednego ciągu; Aplikacja automatycznie analizuje pojedynczy ciąg i wprowadza odpowiednie informacje do odpowiedniej właściwości.</span><span class="sxs-lookup"><span data-stu-id="c2cc6-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="c2cc6-107">Dla uproszczenia w tym przykładzie użyto aplikacji konsolowej z interfejsem wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c2cc6-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2cc6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2cc6-108">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="c2cc6-109">Gdy poprzedni kod jest wykonywany, użytkownik zostanie poproszony o podanie nazwiska i adresu.</span><span class="sxs-lookup"><span data-stu-id="c2cc6-109">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="c2cc6-110">Aplikacja umieszcza informacje w odpowiednich właściwościach i wyświetla informacje z powrotem do użytkownika, tworząc pojedynczy ciąg, który wyświetla miasto, Województwo i informacje o kodzie POCZTOWYm.</span><span class="sxs-lookup"><span data-stu-id="c2cc6-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cc6-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2cc6-111">See also</span></span>

- [<span data-ttu-id="c2cc6-112">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="c2cc6-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

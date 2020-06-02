---
title: Kopiowanie istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 392490d04ff713529d501e199ac2496ff37de1a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289216"
---
# <a name="copy-existing-nodes"></a>Kopiowanie istniejących węzłów
Istnieje wiele metod i właściwości w Document Object Model XML (DOM), których można użyć do wybrania węzła, takiego jak **SelectSingleNode**, **ChildNodes [int i]**, **Attributes [int i]**. Po wybraniu węzła można wstawić go do drzewa przy użyciu jednej z metod INSERT, które działają dla danego typu węzła. Jedynym ograniczeniem do wstawiania węzła do drzewa jest to, że dokument nadal musi być poprawnie sformułowany po wstawieniu węzła. Gdy istniejący węzeł zostanie wstawiony do drzewa DOM, zostaje usunięty z jego pierwotnej pozycji i dodany do jego pozycji docelowej.  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)

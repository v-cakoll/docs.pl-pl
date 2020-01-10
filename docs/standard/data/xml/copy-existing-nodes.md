---
title: Kopiowanie istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: fb9ccd7b16d00355ba87bb32f5447906feeecd94
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711067"
---
# <a name="copy-existing-nodes"></a>Kopiowanie istniejących węzłów
Istnieje wiele metod i właściwości w Document Object Model XML (DOM), których można użyć do wybrania węzła, takiego jak **SelectSingleNode**, **ChildNodes [int i]** , **Attributes [int i]** . Po wybraniu węzła można wstawić go do drzewa przy użyciu jednej z metod INSERT, które działają dla danego typu węzła. Jedynym ograniczeniem do wstawiania węzła do drzewa jest to, że dokument nadal musi być poprawnie sformułowany po wstawieniu węzła. Gdy istniejący węzeł zostanie wstawiony do drzewa DOM, zostaje usunięty z jego pierwotnej pozycji i dodany do jego pozycji docelowej.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

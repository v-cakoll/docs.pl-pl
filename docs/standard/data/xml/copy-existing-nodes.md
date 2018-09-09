---
title: Kopiowanie istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252873"
---
# <a name="copy-existing-nodes"></a>Kopiowanie istniejących węzłów
Istnieje wiele metod i właściwości w XML modelu DOM (Document Object) można użyć, wybierz węzeł, takich jak **SelectSingleNode**, **ChildNodes [int i]**, **atrybutów [int i]**. Po wybraniu węzła można wstawić jej do drzewa za pomocą jednej z metod wstawiania, współpracujących dla tego typu określonego węzła. Jedynym ograniczeniem do wstawiania węzeł w drzewie jest, że dokument musi być poprawnie sformułowany po wstawieniu węzła. Gdy istniejący węzeł jest wstawiany do drzewa DOM, jest usuwane z jego pierwotnej pozycji i dodane do miejsca docelowego.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

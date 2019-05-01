---
title: Kopiowanie istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864133"
---
# <a name="copy-existing-nodes"></a>Kopiowanie istniejących węzłów
Istnieje wiele metod i właściwości w XML modelu DOM (Document Object) można użyć, wybierz węzeł, takich jak **SelectSingleNode**, **ChildNodes [int i]**, **atrybutów [int i]**. Po wybraniu węzła można wstawić jej do drzewa za pomocą jednej z metod wstawiania, współpracujących dla tego typu określonego węzła. Jedynym ograniczeniem do wstawiania węzeł w drzewie jest, że dokument musi być poprawnie sformułowany po wstawieniu węzła. Gdy istniejący węzeł jest wstawiany do drzewa DOM, jest usuwane z jego pierwotnej pozycji i dodane do miejsca docelowego.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

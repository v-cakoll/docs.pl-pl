---
title: Skopiuj istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e7f5638d0d1f7bf450be526d7c295d4bb6a79eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567916"
---
# <a name="copy-existing-nodes"></a>Skopiuj istniejących węzłów
Istnieje wiele metod i właściwości w XML modelu DOM (Document Object) można wybrać węzła, takiej jak **SelectSingleNode**, **ChildNodes [int i]**, **atrybutów [int i]**. Po wybraniu węzła można wstawić je do drzewa przy użyciu jednej z metod wstawiania, które działają dla tego typu określonego węzła. Tylko ograniczenie do wstawiania węzeł w drzewie jest czy dokument nadal należy poprawnie sformułowanym po wstawieniu węzła. Po wstawieniu istniejący węzeł w drzewie DOM, jest usunięte z oryginalnej pozycji i dodane do miejsca docelowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

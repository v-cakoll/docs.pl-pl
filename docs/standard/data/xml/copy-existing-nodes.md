---
title: "Skopiuj istniejących węzłów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c026d9f825375d74d53d5cc46969ff0f713bab1c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="copy-existing-nodes"></a>Skopiuj istniejących węzłów
Istnieje wiele metod i właściwości w XML modelu DOM (Document Object) można wybrać węzła, takiej jak **SelectSingleNode**, **ChildNodes [int i]**, **atrybutów [int i]**. Po wybraniu węzła można wstawić je do drzewa przy użyciu jednej z metod wstawiania, które działają dla tego typu określonego węzła. Tylko ograniczenie do wstawiania węzeł w drzewie jest czy dokument nadal należy poprawnie sformułowanym po wstawieniu węzła. Po wstawieniu istniejący węzeł w drzewie DOM, jest usunięte z oryginalnej pozycji i dodane do miejsca docelowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

---
title: Weryfikacja nazw elementów i atrybutów XML podczas tworzenia nowych węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 7c99ffa9d139d94d26c562cb1668f1b855bed32d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709949"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Weryfikacja nazw elementów i atrybutów XML podczas tworzenia nowych węzłów
Document Object Model XML (DOM) sprawdza poprawność nazw podczas tworzenia nowych węzłów elementów lub węzłów atrybutów. Jeśli nazwy zawierają niedozwolone znaki, zgłaszany jest wyjątek. Aby upewnić się, że nazwy są prawidłowe i zakodowane prawidłowo, należy użyć klasy **XmlConvert** do zakodowania nazwy i zdekodować ją z powrotem na poziomie aplikacji. Element **XmlWriter** ma metody, które wykonują dodatkowe zadania w celu zapewnienia, że generowany jest poprawnie sformułowany kod XML.  
  
## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

---
title: 'Instrukcje: Ładowanie i zwalnianie zestawów (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: adfe23c2c70b1f49e23fb7c3866c8dac5c9c09ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549707"
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Instrukcje: Ładowanie i zwalnianie zestawów (Visual Basic)
Zestawy odwołuje się program automatycznie zostaną załadowane w czasie kompilacji, ale jest również możliwe do załadowania określonych zestawów do bieżącej domeny aplikacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Nie ma możliwości wyładować poszczególnych zestawów bez rozładowywania wszystkich domen aplikacji, które go zawierają. Nawet wtedy, gdy zestaw wykracza poza zakres, plik zestawu rzeczywiste pozostanie załadowane, dopóki wszystkie domeny aplikacji, które go zawierają są usuwane z pamięci.  
  
 Aby zwolnić niektóre zestawy, a nie innych, należy rozważyć tworzenie nowej domeny aplikacji, wykonywanie kodu w tej domenie i następnie zwolnienie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Ładowanie zestawów do domeny aplikacji  
  
1.  Użyj obciążenia jedną z kilku metod zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection>. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Aby zwolnienie domeny aplikacji  
  
1.  Nie ma możliwości wyładować poszczególnych zestawów bez rozładowywania wszystkich domen aplikacji, które go zawierają. Użyj `Unload` metody z <xref:System.AppDomain> wyładować domen aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Zobacz także
- [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [Instrukcje: Ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)

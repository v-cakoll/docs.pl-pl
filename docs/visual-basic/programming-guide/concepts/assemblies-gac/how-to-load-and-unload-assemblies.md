---
title: 'Porady: ładowanie i zwalnianie zestawów (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: 1cec7a7e15843874b65cf5d2f3a23b8e644a26d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640573"
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Porady: ładowanie i zwalnianie zestawów (Visual Basic)
Zestawy odwołuje się program automatycznie zostaną załadowane w czasie kompilacji, ale jest również możliwe ładowanie określonych zestawów do bieżącej domeny aplikacji w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces. Nawet wtedy, gdy zestaw wykracza poza zakres, plik zestawu rzeczywiste pozostanie załadować dopóki wszystkie domeny aplikacji, które zawierałoby proces są usuwane z pamięci.  
  
 Aby zwolnić niektóre zestawy, a innych nie, należy rozważyć tworzenia nowej domeny aplikacji, wykonywanie kodu w tej domenie i następnie zwalnianie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Aby załadować zestawu do domeny aplikacji  
  
1.  Użyj załadować jedną z kilku metod zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection>. Aby uzyskać więcej informacji, zobacz [porady: Ładuj zestawy do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Aby zwolnić domeny aplikacji  
  
1.  Nie istnieje sposób zwolnić poszczególnych zestawów bez zwalniania wszystkich domen aplikacji, które zawierałoby proces. Użyj `Unload` metody z <xref:System.AppDomain> można zwolnić domeny aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zwolnienie domeny aplikacji](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Instrukcje: ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)

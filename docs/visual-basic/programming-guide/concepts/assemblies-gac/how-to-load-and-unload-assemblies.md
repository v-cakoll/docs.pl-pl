---
title: "Porady: ładowanie i zwalnianie zestawów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd52a1094dba16c7e1bcba5bface9e13747cd4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Koncepcje programowania](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Porady: ładowanie zestawów do domeny aplikacji](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)

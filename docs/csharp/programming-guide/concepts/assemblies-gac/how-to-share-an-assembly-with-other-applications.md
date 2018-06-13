---
title: 'Porady: dzielenie się zestawem z innymi aplikacjami (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: beadd6adb176c3fd4e6dde94d95194aea790a2fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324125"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Porady: dzielenie się zestawem z innymi aplikacjami (C#)
Zestawy mogą być prywatne lub współużytkowane: domyślnie większości programów proste składają się z zestaw prywatny, ponieważ nie są one przeznaczone do użycia przez inne aplikacje.  
  
 Aby można było dzielenie się zestawem z innymi aplikacjami, należy umieścić w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Udostępnianie zestawów  
  
1.  Utwórz używanego zestawu. Aby uzyskać więcej informacji, zobacz [tworzenie zestawów](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Przypisz silnej nazwy do używanego zestawu. Aby uzyskać więcej informacji, zobacz [porady: podpisać zestaw o silnej nazwie](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Informacje o wersji należy przypisać do używanego zestawu. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4.  Dodaj użytkownika zestawu w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Dostęp do tych typów zawartych w zestawie z innych aplikacji. Aby uzyskać więcej informacji, zobacz [porady: odwołanie zestawu Strong-Named](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Programowanie za pomocą zestawów](../../../../framework/app-domains/programming-with-assemblies.md)

---
title: 'Porady: dzielenie się zestawem z innymi aplikacjami (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 413eb5e021c782db05abd454ebfa4e7cb1a1abcb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512911"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Porady: dzielenie się zestawem z innymi aplikacjami (C#)
Zestawy mogą być prywatne lub udostępnione: domyślnie większości programów proste składają się z zestawu prywatnego, ponieważ nie są przeznaczone do użycia przez inne aplikacje.  
  
 Aby można było dzielenie się zestawem z innymi aplikacjami, muszą być umieszczone w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Współużytkowanie zestawu  
  
1.  Utwórz zestaw. Aby uzyskać więcej informacji, zobacz [tworzenia zestawów](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Do zestawu, należy przypisać silną nazwę. Aby uzyskać więcej informacji, zobacz [porady: podpisywanie zestawu za pomocą silnej nazwy](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Informacje o wersji należy przypisać do swojego zestawu. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4.  Dodaj zestaw do globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Dostęp do typów są zawarte w zestawie z innych aplikacji. Aby uzyskać więcej informacji, zobacz [porady: odwołanie do zestawu Strong-Named](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
- [Programowanie za pomocą zestawów](../../../../framework/app-domains/programming-with-assemblies.md)

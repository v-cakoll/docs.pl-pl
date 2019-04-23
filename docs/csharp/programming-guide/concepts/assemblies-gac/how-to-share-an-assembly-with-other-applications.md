---
title: 'Instrukcje: Dzielenie się zestawem z innymi aplikacjami (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314792"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Instrukcje: Dzielenie się zestawem z innymi aplikacjami (C#)
Zestawy mogą być prywatne lub udostępnione: domyślnie większości programów proste składają się z zestawu prywatnego, ponieważ nie są przeznaczone do użycia przez inne aplikacje.  
  
 Aby można było dzielenie się zestawem z innymi aplikacjami, muszą być umieszczone w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Współużytkowanie zestawu  
  
1. Utwórz zestaw. Aby uzyskać więcej informacji, zobacz [tworzenia zestawów](../../../../framework/app-domains/create-assemblies.md).  
  
2. Do zestawu, należy przypisać silną nazwę. Aby uzyskać więcej informacji, zobacz [jak: Podpisywanie zestawu silną nazwą](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3. Informacje o wersji należy przypisać do swojego zestawu. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4. Dodaj zestaw do globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5. Dostęp do typów są zawarte w zestawie z innych aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Odwołanie do zestawu o silnej nazwie](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
- [Programowanie za pomocą zestawów](../../../../framework/app-domains/programming-with-assemblies.md)

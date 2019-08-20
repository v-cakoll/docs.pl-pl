---
title: 'Instrukcje: Udostępnianie zestawu innym aplikacjom (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595730"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Instrukcje: Udostępnianie zestawu innym aplikacjom (C#)
Zestawy mogą być prywatne lub udostępnione: Domyślnie większość prostych programów składa się z zestawu prywatnego, ponieważ nie są przeznaczone do użytku przez inne aplikacje.  
  
 W celu udostępnienia zestawu innym aplikacjom należy umieścić je w [globalnej pamięci podręcznej zestawów](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Udostępnianie zestawu  
  
1. Utwórz zestaw. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów](../../../../framework/app-domains/create-assemblies.md).  
  
2. Przypisz silną nazwę do zestawu. Aby uzyskać więcej informacji, zobacz [jak: Podpisz zestaw silną nazwą](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3. Przypisz informacje o wersji do Twojego zestawu. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../framework/app-domains/assembly-versioning.md).  
  
4. Dodaj swój zestaw do globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [jak: Zainstaluj zestaw w globalnej pamięci podręcznej](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)zestawów.  
  
5. Uzyskaj dostęp do typów zawartych w zestawie z innych aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Odwołuje się do zestawu](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)o silnej nazwie.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../index.md)
- [Programowanie za pomocą zestawów](../../../../framework/app-domains/programming-with-assemblies.md)

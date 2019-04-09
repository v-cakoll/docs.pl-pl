---
title: Zestawy o silnych nazwach
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 72e9e698e510153073515aa891f1ed3b4d7b9886
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081440"
---
# <a name="strong-named-assemblies"></a>Zestawy o silnych nazwach
Nazewnictwo silne zestawu tworzy unikatową tożsamość dla zestawu i może zapobiec konfliktom zestawu.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Co sprawia, że zestawu z silną nazwą?  
 Zestaw o nazwie silne jest generowany przy użyciu klucza prywatnego odpowiadającego kluczowi publicznemu rozpowszechniać za pomocą zestawu i samego montażu. Zestaw zawiera manifest zestawu, który zawiera nazwy i wartości skrótów wszystkich plików, wchodzące w skład zestawu. Zestawy, które mają taką samą nazwę silne powinny być identyczne.  
  
 Zestawy o silnych nazwach mogą się przy użyciu programu Visual Studio lub narzędzie wiersza polecenia. Aby uzyskać więcej informacji, zobacz [jak: Podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) lub [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Po utworzeniu zestawu z silną nazwą zawiera zwykły tekst nazwę zestawu, numer wersji, informacji o kulturze opcjonalne, podpis cyfrowy i klucz publiczny, który odnosi się do prywatnego klucza używanego do podpisywania.  
  
> [!WARNING]
>  Nie należy polegać na silne nazwy dla zabezpieczeń. Zapewniają one tylko unikatową tożsamość.  
  
## <a name="why-strong-name-your-assemblies"></a>Dlaczego silnej nazwy zestawów?  
 Gdy odwołujesz się zestawu z silną nazwą, można oczekiwać, że niektóre korzyści, takie jak przechowywanie wersji i nazewnictwa ochrony. Zestawy o silnych nazwach można zainstalować w globalnej pamięci podręcznej zestawów, który jest wymagany do obsługi niektórych scenariuszy.  
  
 Zestawy o silnych nazwach są przydatne w następujących scenariuszach:  
  
-   Aby włączyć swoje zestawy odwoływać się zestawów o silnych nazwach lub chcesz nadać `friend` dostęp do Twoich zestawów od innych zestawów o silnych nazwach.  
  
-   Aplikacja potrzebuje dostępu do różnych wersji tego samego zestawu. Oznacza to, że potrzebujesz różnych wersji zestawu do załadowania obok siebie w tej samej domenie aplikacji, bez powodowania konfliktów. Na przykład jeśli istnieją inne rozszerzenia interfejsu API w zestawach, które mają tej samej prostej nazwie, silne nazwy zapewnia unikatową tożsamość dla każdej wersji zestawu.  
  
-   Czy chcesz mieć negatywny wpływ na wydajność aplikacji przy użyciu swoim zestawie, więc chcesz zestawie, który ma być niezależne od domeny. Wymaga to silne nazwy, ponieważ zestaw niezależne od domeny musi być zainstalowany w globalnej pamięci podręcznej.  
  
-   Jeśli chcesz scentralizować obsługi dla aplikacji, stosując zasady wydawcy, oznacza to zestaw musi być zainstalowany w globalnej pamięci podręcznej.  
  
 Jeśli jesteś deweloperem typu open source i korzystać z zalet tożsamości zestawu z silną nazwą, należy wziąć pod uwagę ewidencjonowanie klucz prywatny skojarzone z zestawem w systemie kontroli źródła.  
  
## <a name="see-also"></a>Zobacz także

- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Instrukcje: Podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Sn.exe (Narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)

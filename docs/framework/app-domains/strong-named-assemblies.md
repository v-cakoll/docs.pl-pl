---
title: Zestawy o silnych nazwach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1d9fb79fa6c58ada7c342bd1d56281c3fbab900
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strong-named-assemblies"></a>Zestawy o silnych nazwach
Nazewnictwo silne zestaw tworzy unikatową tożsamość zestawu i można zapobiec konfliktom zestawu.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Dzięki czemu zestawu z silną nazwą?  
 Zestaw jest generowany przy użyciu klucza prywatnego, który odpowiada kluczowi publicznemu rozpowszechnianej za pomocą zestawu i zestawu. Zestaw zawiera manifest zestawu, który zawiera nazwy i wartości skrótu wszystkie pliki wchodzące w skład zestawu. Zestawy, które mają taką samą nazwę silne powinny być identyczne.  
  
 Zestawy o silnych nazwach można za pomocą programu Visual Studio lub narzędzia wiersza polecenia. Aby uzyskać więcej informacji, zobacz [porady: podpisać zestaw o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) lub [Sn.exe (narzędzie silnej nazwy)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Po utworzeniu zestawu z silną nazwą zawiera zwykły tekst nazwę zestawu, numer wersji informacji o kulturze opcjonalne, podpisu cyfrowego i klucz publiczny, który odpowiada klucz prywatny używany do podpisywania.  
  
> [!WARNING]
>  Nie należy polegać na silnych nazw zabezpieczeń. Udostępniają one tylko unikatową tożsamość.  
  
## <a name="why-strong-name-your-assemblies"></a>Dlaczego silnej nazwy zestawów użytkownika?  
 W przypadku odwołania zestawu z silną nazwą, można oczekiwać, że niektóre korzyści, takich jak przechowywanie wersji i nazewnictwa ochrony. Zestawy o silnych nazwach można zainstalować w globalnej pamięci podręcznej zestawów, który jest wymagany na potrzeby niektórych scenariuszy.  
  
 Zestawy o silnych nazwach są przydatne w następujących scenariuszach:  
  
-   Aby włączyć ponownie zestawy można odwoływać się zestawy o silnych nazwach lub chcesz nadać `friend` dostęp do Twojego zestawy od innych zestawów o silnych nazwach.  
  
-   Aplikacja potrzebuje dostępu do różnych wersji tego samego zestawu. Oznacza to, że należy różnych wersji zestawu do załadowania obok siebie w tej samej domenie aplikacji bez konfliktu. Na przykład jeśli istnieją inne rozszerzenia interfejsu API w zestawy, które mają taką samą prostą nazwę, silne nazwy zapewnia unikatową tożsamość dla każdej wersji zestawu.  
  
-   Czy chcesz mieć negatywny wpływ na wydajność aplikacji, korzystając z zestawu tak ma zestaw jako neutralny dla domen. Wymaga to silne nazwy zestawu neutralne dla domen musi zostać zainstalowany w globalnej pamięci podręcznej zestawów.  
  
-   Umożliwia scentralizowane obsługi dla aplikacji, stosując zasady wydawcy, co oznacza zestawu musi być zainstalowany w globalnej pamięci podręcznej zestawów.  
  
 Jeśli jesteś deweloperem open source i korzystać z zalet tożsamości zestawu z silną nazwą, należy wziąć pod uwagę ewidencjonowanie klucz prywatny skojarzony z zestawem do systemu kontroli źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 [Instrukcje: podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)

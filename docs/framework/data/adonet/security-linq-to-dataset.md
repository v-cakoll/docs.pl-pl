---
title: Zabezpieczenia (LINQ do DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 43d529b6f74b58783cc2aaa7a81b2f75790b4e40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-linq-to-dataset"></a>Zabezpieczenia (LINQ do DataSet)
W tym temacie omówiono problemy z zabezpieczeniami w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Przekazywanie kwerendy do niezaufany składnik  
 A [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania mogą być sformułowane w jeden punkt programu i wykonywane w innym. W momencie, gdzie zapytanie jest sformułowany zapytania można odwoływać się do elementów, które jest widoczna w tym momencie, takich jak prywatne elementy członkowskie klasy należącą do wywoływania metody lub symbole reprezentujących zmienne lokalne/argumentów. W czasie wykonywania zapytania skutecznie będą mogli uzyskać dostęp do tych elementów członkowskich, które zostały odwołuje się zapytanie o formułowanie, nawet jeśli kod wywołujący nie ma wgląd w ich. Kod, który wykonuje zapytanie nie ma dowolnego widoczność dodany, w tym nie można go wybrać, co dostępu do. Będą mieli dostęp do ściśle co zapytanie uzyskuje dostęp do, wyłącznie za pośrednictwem samą kwerendę.  
  
 Oznacza to, że przekazując odwołanie do zapytania do innego fragmentu kodu składnika odbieranie zapytania jest jest zaufana z dostępem do wszystkich publicznych i prywatnych elementów członkowskich, które zapytanie odwołuje się do. Ogólnie rzecz biorąc [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania nie powinny być przekazywane do niezaufanych składników, jeśli zapytanie ma dokładnie skonstruowane tak, aby nie uwidacznia informacje, które powinny być przechowywane w prywatnej.  
  
## <a name="external-input"></a>Zewnętrzny  
 Aplikacje często zająć zewnętrzny (od użytkownika lub innego agenta zewnętrznych) i wykonywania akcji w oparciu o te dane wejściowe.  W przypadku liczby [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], aplikacja może utworzyć kwerendy w określony sposób, na podstawie zewnętrzny lub Użyj zewnętrznego danych wejściowych w zapytaniu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania akceptuje wszędzie parametrów, że literały są akceptowane. Deweloperzy aplikacji należy używać sparametryzowanych zapytań, zamiast iniekcję literały z zewnętrznego agenta bezpośrednio do zapytania.  
  
 Wszystkie wejściowych bezpośrednio lub pośrednio pochodzi od użytkownika lub zewnętrznego agenta może mieć zawartość, która używa składni języka docelowego w celu wykonania akcji nieautoryzowanego. Jest to nazywane atak iniekcji kodu SQL o nazwie po wzorzec ataku, gdzie jest języka Transact-SQL w języku docelowym. Dane wejściowe użytkownika bezpośrednio do zapytania służy do tabeli bazy danych, "odmowa usługi" lub modyfikowania rodzaj wykonywanej operacji. Mimo że zapytanie jest możliwe w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], odbywa się za pośrednictwem interfejsu API modelu obiektu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania nie składają się przy użyciu manipulowanie ciągami lub łączenia, w języku Transact-SQL, i nie są podatne na ataki w tym sensie, tradycyjnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)

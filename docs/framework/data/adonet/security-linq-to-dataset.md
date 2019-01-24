---
title: Zabezpieczenia (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: e0b71dd3628e0bbc4c11e7b9f62a4833ce6fa811
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604134"
---
# <a name="security-linq-to-dataset"></a>Zabezpieczenia (LINQ to DataSet)
W tym temacie omówiono problemy z zabezpieczeniami w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Przekazywanie zapytania do niezaufany składnik  
 A [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, które mogą być sformułowane w jeden punkt programu i wykonywane w innym. W momencie, gdy zapytanie jest sformułowany zapytanie można odwoływać się do dowolnego elementu, który jest widoczny w tym momencie, takich jak prywatne składowe klasy, która należy do wywoływania metody lub symbole reprezentujących zmienne lokalne/argumentów. W czasie wykonywania zapytania skutecznie będzie dostępu do tych członków, które zostały określone przez zapytanie w skład, nawet jeśli kod wywołujący nie ma wgląd w ich. Kod, który wykonuje zapytanie nie widzą dowolnego dodano, że nie można go wybrać, co dostęp do. Będą mogli korzystać wyłącznie z co zapytanie uzyskuje dostęp i tylko poprzez samo zapytanie.  
  
 Oznacza to, że przez przekazanie odwołanie do kwerendy do innej części kodu składnika odbieranie zapytania są ufa z dostępem do wszystkie publiczne i prywatne składowe, które zapytanie odwołuje się do. Ogólnie rzecz biorąc [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania nie powinny być przekazywane do niezaufanych składników, chyba że zapytania została starannie skonstruowana tak, aby nie uwidacznia informacje, które powinny być przechowywane w prywatnej.  
  
## <a name="external-input"></a>Zewnętrzny  
 Aplikacje często akceptują dane wejściowe w zewnętrznych (z lub innego zewnętrznego agenta użytkownika) i wykonywać akcje w oparciu o te dane wejściowe.  W przypadku właściwości [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], aplikacja może utworzyć zapytania w określony sposób, na podstawie zewnętrznych danych wejściowych lub Użyj zewnętrznego danych wejściowych w zapytaniu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania akceptować wszędzie, gdzie parametry, że literały są akceptowane. Deweloperzy aplikacji należy używać sparametryzowanych zapytań, zamiast iniekcji literały z zewnętrznego agenta bezpośrednio do zapytania.  
  
 Wszystkie dane wejściowe bezpośrednio lub pośrednio pochodzi od użytkownika lub zewnętrznego agenta może mieć zawartość, która wykorzystuje składnię języka docelowego w celu wykonywania akcji nieautoryzowanego. Jest to nazywane ataku polegającego na iniekcji SQL, nazwana wzorca ataku, gdzie jest języka Transact-SQL w języku docelowym. Dane wejściowe użytkownika, które są wstrzykiwane bezpośrednio do zapytania służy do porzucić tabeli bazy danych, powodujących typu "odmowa usługi" lub w przeciwnym razie Zmień rodzaj wykonywanej operacji. Mimo że w kompozycją zapytań [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], odbywa się za pośrednictwem interfejsu API modelu obiektu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania nie składają się przy użyciu manipulowanie ciągami lub łączenia, ponieważ znajdują się w instrukcji Transact-SQL i nie są narażone na ataki przez iniekcję SQL w tradycyjnym rozumieniu.  
  
## <a name="see-also"></a>Zobacz także
- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)

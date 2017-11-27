---
title: "Pamięć automatycznego zarządzania i odzyskiwanie pamięci"
description: "Dowiedz się, jak automatyczne pamięci zarządzania jest jednym z usług, które zawiera środowisko uruchomieniowe języka wspólnego podczas wykonania kodu zarządzanego."
keywords: .NET, .NET core
author: dotnet-bot
ms.author: dotnetcontent
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d095b0b6-2454-4e23-80b4-c9e8a447116c
ms.openlocfilehash: 30bcf08ebb4e05706d5b25e2f805474dd1ee428e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="automatic-memory-management-and-garbage-collection"></a>Pamięć automatycznego zarządzania i odzyskiwanie pamięci

Automatyczne zarządzanie pamięcią jest jednym z usług, które zawiera środowisko uruchomieniowe języka wspólnego podczas wykonania kodu zarządzanego. Środowisko uruchomieniowe języka wspólnego przez moduł Garbage Collector zarządza alokacji i wersji pamięci dla aplikacji. Z perspektywy deweloperów oznacza to, że podczas tworzenia zarządzanych aplikacji nie trzeba pisać kodu wykonującego zadania zarządzania pamięcią. Funkcjonalność automatycznego zarządzania pamięcią może wyeliminować typowe problemy, takie jak zapominanie o zwalnianiu obiektów z pamięci, powodowanie przecieków pamięci czy próba uzyskania dostępu do pamięci dla obiektu, który został już zwolniony z pamięci. W tej części opisano, jak moduł odśmiecania pamięci przydziela i zwalnia pamięć.

## <a name="allocating-memory"></a>Przydzielanie pamięci

Podczas inicjowania nowego procesu środowisko uruchomieniowe rezerwuje dla niego ciągły region przestrzeni adresowej. Zarezerwowana przestrzeń adresowa jest nazywana „zarządzanym stosem”. Zarządzany stos zawiera wskaźnik do adresu, w którym zostanie przydzielony następny obiekt ze stosu. Początkowo wskaźnik jest ustawiony na adres podstawowy zarządzanego stosu. Wszystkie typy referencyjne są przydzielone na stercie zarządzanej. Gdy aplikacja tworzy pierwszy typ referencyjny, jest dla niego rezerwowana pamięć pod podstawowym adresem zarządzanego stosu. Podczas tworzenia następnego obiektu moduł odśmiecania pamięci przydziela mu pamięć w przestrzeni adresowej następującej bezpośrednio po pierwszym obiekcie. Tak długo, jak jest dostępna przestrzeń adresowa, moduł odśmiecania pamięci przydziela w ten sposób miejsce nowym obiektom.

Przydzielanie pamięci z zarządzanego stosu jest szybsze niż niezarządzane przydzielanie pamięci. Ponieważ środowisko uruchomieniowe przydziela obiektowi pamięć poprzez dodanie wartości do wskaźnika, operacja przebiega niemal tak samo szybko jak alokacja pamięci ze stosu. Ponadto nowe obiekty, którym system przydziela kolejne sekcje pamięci, są zapisywane kolejno w sposób ciągły w zarządzanym stosie, dlatego aplikacja ma do nich błyskawiczny dostęp.

## <a name="releasing-memory"></a>Zwalnianie pamięci

Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały. Gdy moduł odśmiecania wykonuje ten proces, zwalnia pamięć zajmowaną przez obiekty, które nie są już używane przez aplikację. Ustalenia, które obiekty są bezużyteczne, dokonuje poprzez analizę głównych obiektów aplikacji. Każda aplikacja ma zbiór obiektów głównych. Każdy obiekt główny odwołuje się do obiektu w zarządzanym stosie albo przyjmuje wartość null. Katalogi główne aplikacji obejmują pól statycznych, zmienne lokalne i parametry stosu wątku i rejestruje procesora CPU. Moduł zbierający elementy bezużyteczne ma dostęp do listy aktywnych głównych, których obsługa kompilatora just-in-time (JIT) i środowiska uruchomieniowego. Za pomocą tej listy sprawdza obiekty główne aplikacji i generuje wykres przedstawiający wszystkie obiekty dostępne z obiektów głównych.

Obiekty nieobecne na liście są nieosiągalne z obiektów głównych aplikacji. Moduł odśmiecania pamięci uznaje niedostępne obiekty za śmieci i zwalnia przydzieloną im pamięć. Podczas wyrzucania elementów moduł odśmiecania pamięci analizuje zarządzany stos w poszukiwaniu bloków przestrzeni adresowej zajmowanych przez nieosiągalne obiekty. Po wykryciu niedostępnego obiektu moduł odśmiecania za pomocą funkcji kopiowania pamięci kompaktuje dostępne obiekty wewnątrz pamięci i jednoczenie zwalnia bloki przestrzeni adresowej przydzielone dotychczas nieosiągalnym obiektom. Po skompaktowaniu pamięci osiągalnych obiektów moduł odśmiecania pamięci dokonuje niezbędnych korekt wskaźników, tak aby obiekty główne aplikacji wskazywały obiekty w ich nowych lokalizacjach. Ponadto ustawia wskaźnik zarządzanego stosu za ostatnim dostępnym obiektem. Należy pamiętać, że pamięć jest kompaktowana tylko w przypadku, gdy proces wyrzucania bezużytecznych elementów wykryje znaczącą liczbę nieosiągalnych obiektów. Jeśli żaden obiekt w zarządzanym stosie nie wymaga wyrzucenia, nie ma też potrzeby kompaktowania pamięci.

W celu poprawy wydajności działania środowisko uruchomieniowe przydziela pamięć dużym obiektom w oddzielnym stosie. Moduł odśmiecania pamięci automatycznie zwalnia pamięć dla dużych obiektów. Jednak aby uniknąć przenoszenia dużych obiektów w pamięci, ta pamięć nie jest kompaktowana.

## <a name="generations-and-performance"></a>Generacje i wydajność

Aby zoptymalizować wydajność modułu zbierającego elementy bezużyteczne, sterty zarządzanej jest podzielony na trzy generacje: 0, 1 i 2. Algorytm wyrzucania elementów bezużytecznych w środowisku uruchomieniowym opiera się na kilku uogólnieniach, które wypracowano w branży oprogramowania komputerowego po wielu eksperymentach ze schematami wyrzucania. Po pierwsze, kompaktowanie pamięci dla części zarządzanego stosu jest szybsze niż dla całego stosu. Po drugie, nowsze obiekty mają krótsze okresy istnienia, a starsze — dłuższe. Po trzecie, nowsze obiekty są zazwyczaj powiązane ze sobą, a aplikacja uzyskuje do nich dostęp mniej więcej w tym samym czasie.

Moduł odśmiecania pamięci w środowisku uruchomieniowym zapisuje nowe obiekty pod generacją 0. Obiekty utworzone wcześniej w okresie istnienia aplikacji i nieusunięte przez moduł odśmiecania trafiają na wyższy poziom, do generacji 1 i 2. Proces podwyższania poziomu obiektu opisano w dalszej części tego tematu. Ponieważ kompaktowanie części zarządzanego stosu jest szybsze niż całego stosu, ten schemat pozwala modułowi odśmiecania pamięci w każdej sesji odśmiecania zwalniać pamięć tylko w konkretnej generacji, a nie w całym zarządzanym stosie.

W praktyce moduł odśmiecania pamięci wyrzuca elementy bezużyteczne po zapełnieniu się generacji 0. Gdy aplikacja próbuje utworzyć nowy obiekt w sytuacji zapełnionej generacji 0 moduł odśmiecania pamięci wykrywa, że w generacji 0 brakuje przestrzeni adresowej, którą można by przydzielić obiektowi. Chcąc zwolnić mu przestrzeń w generacji 0, moduł odśmiecania inicjuje proces wyrzucania bezużytecznych elementów. Rozpoczyna od zbadania obiektów w generacji 0, a nie wszystkich obiektów w zarządzanym stosie. To najbardziej wydajne podejście, ponieważ nowe obiekty mają zazwyczaj krótkie okresy istnienia i podczas operacji wyrzucania okazuje się, że wiele obiektów w generacji 0 nie jest już używanych przez aplikację. Ponadto często wyrzucanie elementów z samej generacji 0 zwalnia dość pamięci, aby aplikacja mogła kontynuować tworzenie nowych obiektów.

Po moduł garbage collector wykonuje kolekcji pokolenia 0, kompaktuje pamięci dla obiekt dostępny, zgodnie z objaśnieniem w [zwolnienie pamięci](#releasing-memory) wcześniej w tym temacie. Następnie podwyższa tym obiektom poziom i uznaje tę część zarządzanego stosu za generację 1. Ponieważ obiekty, które pozostały po procesie wyrzucania elementów, zwykle mają dłuższe okresy istnienia, podwyższenie im poziomu o generację jest jak najbardziej uzasadnione. W rezultacie moduł odśmiecania pamięci nie musi badać obiektów w generacjach 1 i 2 podczas każdej sesji odśmiecania generacji 0.

Gdy moduł odśmiecania pamięci zakończy pierwszą sesję wyrzucania elementów z generacji 0 i pozostałym obiektom podwyższy poziom do generacji 1, wszystkie elementy pozostałe w zarządzanym stosie uznaje za należące do generacji 0. Kontynuuje przydzielanie pamięć nowym obiektom w generacji 0, aż generacja się zapełni i trzeba będzie wykonać kolejne wyrzucanie. W tym momencie aparat optymalizacji w module odśmiecania pamięci stwierdza, czy jest konieczne badanie obiektów w starszych generacjach. Jeśli na przykład wyrzucanie elementów z generacji 0 nie powoduje odzyskania wystarczającej ilości pamięci, aby aplikacja mogła pomyślnie ukończyć próbę utworzenia nowego obiektu, moduł odśmiecania może przeprowadzić wyrzucanie bezużytecznych elementów w generacji 1, a następnie w generacji 2. Gdy to nie spowoduje odzyskania wystarczającej ilości pamięci, moduł odśmiecania pamięci może wykonać tę operację ponownie kolejno w generacjach 2, 1 i 0. Po każdej sesji moduł kompaktuje osiągalne obiekty w generacji 0 i podwyższa ich poziom do generacji 1. Obiekty w generacji 1, które nie zostały wyrzucone, są przenoszone do generacji 2. Ponieważ moduł odśmiecania pamięci obsługuje tylko trzy generacje, obiekty w generacji 2 nieusunięte po sesji wyrzucania pozostają w tej generacji, aż w przyszłych sesjach aparat uzna je za niedostępne.

## <a name="releasing-memory-for-unmanaged-resources"></a>Zwalnianie pamięci dla niezarządzanych zasobów

W przypadku większości obiektów tworzonych przez aplikację moduł odśmiecania pamięci potrafi automatycznie wykonywać niezbędne zadania zarządzania pamięcią. Zasoby niezarządzane wymagają jednak jawnego usuwania z pamięci. Najpopularniejszym typem niezarządzanego zasobu jest obiekt opakowujący zasób systemu operacyjnego, taki jak dojście do pliku, uchwyt okna lub połączenie sieciowe. Mimo iż moduł odśmiecania pamięci jest w stanie śledzić okres istnienia zarządzanego obiektu hermetyzującego niezarządzany zasób, nie wie, jak dokładnie ma usuwać ten zasób z pamięci. Podczas tworzenia obiektu, który hermetyzuje zasób niezarządzany, zaleca się podanie niezbędne kod, aby wyczyścić niezarządzanego zasobu w publicznej `Dispose` metody. Zapewniając `Dispose` metody umożliwiają użytkownikom obiektu jawnie wolne pamięci po zakończeniu z obiektem. Korzystając z obiektu, który hermetyzuje zasób niezarządzany, należy zwrócić uwagę `Dispose` i wywołać ją w razie potrzeby. Aby uzyskać więcej informacji o czyszczeniu zasoby niezarządzane i przykład stosowania wzorca projektowego `Dispose`, zobacz [wyrzucanie elementów bezużytecznych w programie .NET](index.md).

## <a name="see-also"></a>Zobacz też

[System.GC](xref:System.GC)

[Wyrzucanie elementów bezużytecznych w .NET](index.md)


---
title: Kopiowanie i przypinanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11739d35d3a6d845feb1f6d9544f6ea347a9942d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="copying-and-pinning"></a>Kopiowanie i przypinanie
Podczas organizowania danych, międzyoperacyjnego organizatora można skopiować lub przypiąć dane są przekazywane. Kopiowanie danych umieszcza kopię danych z jednej lokalizacji pamięci w innej lokalizacji pamięci. Na poniższej ilustracji przedstawiono różnice między kopiowanie typu wartości i kopiowanie typ przekazany przez odwołanie z zarządzanych do niezarządzanych pamięci.  
  
 ![Wartość typów przekazywane według wartości i według odwołania](../../../docs/framework/interop/media/interopmarshalcopy.gif "interopmarshalcopy")  
Typy wartości przekazywane według wartości i według odwołania  
  
 Argumenty metody przekazany przez wartość są przekazywane do kodu niezarządzanego jako wartości na stosie. Proces kopiowania jest bezpośrednie. Argumenty przekazywane przez odwołanie są przekazywane jako wskaźników na stosie. Typy odwołań również są przekazywane według wartości i według odwołania. Jak pokazano na poniższej ilustracji, typu odwołania przekazany przez wartość są kopiowane lub przypięty.  
  
 ![Współdziałanie z COM](../../../docs/framework/interop/media/interopmarshalpin.gif "interopmarshalpin")  
Typy odwołań przekazywane według wartości i według odwołania  
  
 Przypinanie tymczasowo blokuje danych w jego bieżącej lokalizacji pamięci, w związku z tym zachowaniu z przeniesieniu przez moduł Garbage Collector środowiska CLR firmy. Organizator PIN danych pozwala zmniejszyć liczbę czynności kopiowania i zwiększyć wydajność. Typ danych określa, czy jest kopiowany lub przypięty podczas organizowania procesu.  Przypinanie jest wykonywana automatycznie podczas marshaling dla obiektów, takich jak <xref:System.String>, ale można też ręcznie przypiąć przy użyciu pamięci <xref:System.Runtime.InteropServices.GCHandle> klasy.  
  
## <a name="formatted-blittable-classes"></a>Klasy sformatowany Kopiowalne  
 Sformatowany [kopiowalne](../../../docs/framework/interop/blittable-and-non-blittable-types.md) klasy wyeliminowaniu układu (sformatowany) i wspólne reprezentację danych zarówno w zarządzanych i niezarządzanych pamięci. Te typy potrzebują przekazywanie, wskaźnik do obiektu w stercie są przekazywane do wywoływany bezpośrednio. Wywoływany, można zmienić zawartość przywoływane przez wskaźnik lokalizacji w pamięci.  
  
> [!NOTE]
>  Wywoływany, można zmienić zawartości pamięci, jeśli parametr jest oznaczony jako Out lub we/wy. Z kolei wywoływany należy unikać zmiany zawartości, gdy parametr ma wartość do organizowania jako w jest to wartość domyślna dla typy kopiowalne sformatowany. Modyfikowanie obiektu w generuje problemy podczas eksportowania tej samej klasy do biblioteki typów i używane do nawiązywania połączeń między apartamentu.  
  
## <a name="formatted-non-blittable-classes"></a>Klasy sformatowany niekopiowalne  
 Sformatowany [niekopiowalne](../../../docs/framework/interop/blittable-and-non-blittable-types.md) klasy wyeliminowaniu układu (sformatowany), ale reprezentację danych różni się w pamięci zarządzane i niezarządzane. Dane można wymagać transformacji w następujących warunkach:  
  
-   Jeśli klasa niekopiowalne jest przekazywane przez wartość, wywoływany otrzymuje wskaźnik kopię struktury danych.  
  
-   Jeśli klasa niekopiowalne jest przekazywane przez odwołanie, wywoływany otrzymuje wskaźnik na wskaźnik do kopiowania struktury danych.  
  
-   Jeśli <xref:System.Runtime.InteropServices.InAttribute> atrybutu jest ustawiona, ta kopia zawsze jest inicjowany z stan wystąpienia, organizowanie odpowiednio do potrzeb.  
  
-   Jeśli <xref:System.Runtime.InteropServices.OutAttribute> atrybutu jest ustawiona, stan jest zawsze kopiowany do wystąpienia przy powrocie organizowanie odpowiednio do potrzeb.  
  
-   Jeśli oba **InAttribute** i **OutAttribute** skonfigurowano obydwie kopie są wymagane. W przypadku pominięcia albo atrybut organizatora zoptymalizować przez wyeliminowanie Kopiuj.  
  
## <a name="reference-types"></a>Typy odwołań  
 Typy odwołań, mogą być przekazywane przez wartości lub według odwołania. Gdy są one przekazywane przez wartość wskaźnika do typu są przekazywane na stosie. Gdy dane są przekazywane przez odwołanie, wskaźnika do wskaźnika do typu są przekazywane na stosie.  
  
 Typy referencyjne mieć warunkowego następujące działania:  
  
-   Jeśli typ referencyjny jest przekazywany przez wartość i ma elementów członkowskich typu niekopiowalne, typy są konwertowane dwa razy:  
  
    -   Gdy argument jest przekazywany do strony niezarządzane.  
  
    -   Na powrót z wywołania.  
  
     Aby uniknąć niepotrzebnie kopiowanie i konwersji, te typy są przekazywane jako w parametrach. Musisz jawnie zastosować **InAttribute** i **OutAttribute** atrybuty do argumentu dla obiekt wywołujący, aby zobaczyć zmiany wprowadzone przez funkcję wywołującą.  
  
-   Jeśli typ referencyjny jest przekazywany przez wartość i ma tylko członkowie typy kopiowalne, można przypiąć podczas przekazywania międzyprocesowego i wszelkie zmiany wprowadzone przez funkcję wywołującą elementy członkowskie tego typu są widoczne dla obiekt wywołujący. Zastosuj **InAttribute** i **OutAttribute** jawnie, jeśli chcesz, aby ten problem. Bez tych atrybutów kierunkową organizatora międzyoperacyjne nie eksportuje kierunkową informacji do biblioteki typów (go eksportuje jak w programie, co jest ustawieniem domyślnym) i może to spowodować problemy z organizowanie między apartamentu COM.  
  
-   Jeśli typ referencyjny jest przekazywana przez odwołanie, jego będzie można zorganizować jako we/wy domyślnie.  
  
## <a name="systemstring-and-systemtextstringbuilder"></a>System.String i elementu System.Text.StringBuilder  
 Gdy dane są przekazywane do kodu niezarządzanego według wartości lub według odwołania, organizator zwykle kopiuje dane w buforze dodatkowej (prawdopodobnie konwertowanie zestawów znaków podczas kopiowania) i przekazuje odwołanie do buforu wywoływany. Chyba, że odwołanie jest **BSTR** przydzielonych za pomocą **SysAllocString**, odwołanie, jest zawsze przydzielana z **CoTaskMemAlloc**.  
  
 Optymalizacji podczas dowolnego typu ciąg jest przekazywane przez wartość (na przykład ciąg znaków Unicode) organizatora przekazuje wywoływany bezpośrednio wskaźnika do zarządzanego ciągów w buforze Unicode wewnętrznego, zamiast go kopiować do bufor nowego.  
  
> [!CAUTION]
>  Jeśli ciąg jest przekazywany przez wartość, wywoływany nigdy nie należy zmienić odwołania przekazany przez organizatora. W ten sposób może spowodować uszkodzenie sterty zarządzanej.  
  
 Gdy <xref:System.String?displayProperty=nameWithType> jest przekazywana przez odwołanie, organizator wpisuje ciąg do dodatkowej buforu przed wykonaniem połączenia. Następnie kopiuje zawartość buforów do nowego ciągu na powrót z wywołania. Ta metoda gwarantuje, że niezmienny ciąg zarządzanych pozostanie niezmieniona.  
  
 Gdy <xref:System.Text.StringBuilder?displayProperty=nameWithType> jest przekazywany przez wartość i przekazuje organizatora odwołaniem do wewnętrznego buforu elementu **StringBuilder** bezpośrednio do obiektu wywołującego. Obiekt wywołujący i wywoływany należy uzgodnić rozmiar buforu. Element wywołujący jest odpowiedzialny za tworzenie **StringBuilder** odpowiedniej długości. Wywoływany musi podjąć niezbędne środki ostrożności, aby upewnić się, że nie jest przepełnienie buforu. **StringBuilder** jest wyjątek do reguły odwołujące się do typów przekazywane przez wartość są przekazywane tak jak parametry domyślnie. Jest on zawsze przekazany jako we/wy.  
  
## <a name="see-also"></a>Zobacz też  
 [Domyślne zachowanie marshalingu](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [Zarządzanie pamięcią z organizatora międzyoperacyjne](http://msdn.microsoft.com/library/417206ce-ee3e-4619-9529-0c0b686c7bee)  
 [Atrybuty kierunkową](http://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)

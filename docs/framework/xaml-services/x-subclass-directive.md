---
title: x:Subclass — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053914"
---
# <a name="xsubclass-directive"></a>x:Subclass — dyrektywa
Modyfikuje zachowanie kompilowania znaczników `x:Class` XAML, gdy jest również udostępniane. Zamiast tworzenia klasy częściowej, która jest oparta na `x:Class`, dostarczony `x:Class` element jest tworzony jako Klasa pośrednicząca, a następnie powinna być oparta na `x:Class`podanej klasie pochodnej.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`namespace`|Opcjonalny. Określa przestrzeń nazw środowiska CLR, `classname`która zawiera. Jeśli `namespace` jest określony, kropka (.) `namespace` oddziela i `classname`.|  
|`classname`|Wymagana. Określa nazwę CLR klasy częściowej, która łączy załadowany kod XAML i związany z kodem dla tego języka XAML. Zobacz uwagi.|  
|`subclassNamespace`|Opcjonalny. Może się różnić od `namespace` tego, czy każda przestrzeń nazw może rozwiązać ten problem. Określa przestrzeń nazw środowiska CLR, `subclassName`która zawiera. Jeśli `subclassName` jest określony, kropka (.) `subclassNamespace` oddziela i `subclassName`.|  
|`subclassName`|Wymagane. Określa nazwę środowiska CLR podklasy.|  
  
## <a name="dependencies"></a>Zależności  
 [dyrektywa x:Class](x-class-directive.md) musi być również podana dla tego samego obiektu i musi być elementem głównym produkcji XAML.  
  
## <a name="remarks"></a>Uwagi  
 `x:Subclass`Użycie jest przeznaczone głównie dla języków, które nie obsługują deklaracji klasy częściowej.  
  
 Klasa używana jako `x:Subclass` nie może być klasą zagnieżdżoną i `x:Subclass` musi odwoływać się do obiektu głównego zgodnie z opisem w sekcji "zależności".  
  
 W przeciwnym razie koncepcyjne znaczenie `x:Subclass` jest niezdefiniowane przez .NET Framework implementację usług XAML. Wynika to z faktu, że zachowanie usług XAML .NET Framework nie określa ogólnego modelu programowania, za pomocą którego są połączone znaczniki XAML i kod zapasowy. Implementacje dalszych koncepcji związanych z `x:Class` programem `x:Subclass` i są wykonywane przez określone platformy, które używają modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML, skompilowanych znaczników i kodu opartego na środowisku CLR. Każda struktura może mieć własne akcje kompilacji, które umożliwiają zachowanie niektórych zachowań lub określonych składników, które muszą być zawarte w środowisku kompilacji. W ramach struktury akcje kompilacji mogą się różnić w zależności od języka CLR, który jest używany w kodzie.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 `x:Subclass`może znajdować się w katalogu głównym strony lub <xref:System.Windows.Application> w katalogu głównym w definicji aplikacji, która już `x:Class`ma. Deklarowanie `x:Subclass` dla dowolnego elementu, innego niż strona lub katalog główny lub określenie, gdzie nie `x:Class` istnieje, powoduje błąd czasu kompilacji.  
  
 Tworzenie klas pochodnych, które działają poprawnie dla `x:Subclass` scenariusza, jest dość skomplikowane. Może być konieczne przeanalizowanie plików pośrednich (plików g produkowanych w folderze obj projektu przez kompilację znaczników z nazwami, które zawierają nazwy plików. XAML). Te pliki pośrednie mogą pomóc określić źródło niektórych konstrukcji programistycznych w sprzężonych klasach częściowych w skompilowanej aplikacji.  
  
 Procedury obsługi zdarzeń w klasie pochodnej muszą być `internal override` (`Friend Overrides` w programie Microsoft Visual Basic), aby przesłonić elementy pośredniczące dla programów obsługi jako utworzone w klasie pośredniej podczas kompilacji. W przeciwnym razie implementacje klas pochodnych ukryją (Shadow) implementację klasy pośredniej i procedury obsługi klasy pośredniczącej nie są wywoływane.  
  
 Podczas definiowania obu `x:Class` i `x:Subclass`, nie trzeba podawać żadnej implementacji dla `x:Class`klasy, do której odwołuje się. Wystarczy nadać mu nazwę przy użyciu `x:Class` atrybutu, aby kompilator miał pewne wskazówki dotyczące klasy, którą tworzy w plikach pośrednich (w tym przypadku kompilator nie wybiera nazwy domyślnej). Można nadać `x:Class` klasie implementację, ale nie jest to typowy scenariusz użycia obu `x:Class` i `x:Subclass`.  
  
## <a name="see-also"></a>Zobacz także

- [x:Class, dyrektywa](x-class-directive.md)
- [Klasy XAML i niestandardowe dla WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)

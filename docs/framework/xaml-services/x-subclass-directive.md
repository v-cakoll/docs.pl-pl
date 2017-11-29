---
title: "x:Subclass — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5c6e91fcecb60dee2577ea62c2313f8b2c7eecbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xsubclass-directive"></a>x:Subclass — dyrektywa
Modyfikuje zachowanie kompilacji znaczników XAML podczas `x:Class` jest również udostępniany. Zamiast tworzenia częściowej klasy, która jest oparta na `x:Class`, dostarczonych `x:Class` zostanie utworzona jako klasa pośrednicząca, a następnie oczekuje na podstawie podanych klasy pochodnej `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`namespace`|Opcjonalny. Określa przestrzeń nazw środowiska CLR, która zawiera `classname`. Jeśli `namespace` określono kropkę (.) oddziela `namespace` i `classname`.|  
|`classname`|Wymagany. Określa nazwę CLR częściowej klasy, która łączy załadować XAML i z kodem dla tego języka XAML. Zobacz uwagi.|  
|`subclassNamespace`|Opcjonalny. Może się różnić od `namespace` Jeśli każdej przestrzeni nazw można rozwiązać drugi. Określa przestrzeń nazw środowiska CLR, która zawiera `subclassName`. Jeśli `subclassName` określono kropkę (.) oddziela `subclassNamespace` i `subclassName`.|  
|`subclassName`|Wymagany. Określa nazwę CLR podklasy.|  
  
## <a name="dependencies"></a>Zależności  
 [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md) należy dostarczyć także na tym samym obiekcie i ten obiekt musi być elementem głównym produkcji XAML.  
  
## <a name="remarks"></a>Uwagi  
 `x:Subclass`użycie jest przeznaczone głównie dla języków, które nie obsługują deklaracji klasy częściowej.  
  
 Użyta jako klasa `x:Subclass` nie może być klasą zagnieżdżoną i `x:Subclass` musi odwoływać się do obiektu głównego, jak opisano w sekcji "Zależności".  
  
 W przeciwnym razie koncepcyjnej znaczenie `x:Subclass` jest niezdefiniowana przez implementację usług .NET Framework XAML. Jest to spowodowane zachowanie usług .NET Framework XAML nie został określony ogólny model programowania przez XAML, które są połączone znaczników i tworzenie kopii kodu. Implementacje dalsze pojęcia związane z `x:Class` i `x:Subclass` są wykonywane przez określone struktur, co umożliwia definiowanie sposobu połączenia znaczników XAML, znaczników skompilowany i na podstawie CLR kodem modele programowania i modeli aplikacji. Każdy framework może mieć własną akcji kompilacji, które udostępnia niektóre działania lub określone składniki, które muszą być zawarte w środowisku kompilacji. W ramach akcji kompilacji można również różnić w zależności od określonego języka środowiska CLR używanej do kodu powiązanego.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 `x:Subclass`można na katalog główny strony lub <xref:System.Windows.Application> głównego definicji aplikacji, który ma już `x:Class`. Deklarowanie `x:Subclass` dla dowolnego elementu innego niż katalog główny strony lub aplikacji lub określanie go, jeśli nie `x:Class` istnieje, powoduje błąd kompilacji.  
  
 Tworzenie pochodnych klas pracy prawidłowe `x:Subclass` scenariusza jest dość złożone. Konieczne może być zbadać plików pośrednich (pliki .g tworzone w folderze obj. projektu przez kompilacji znaczników, z nazwami zawierające .xaml nazwy pliku). Tych plików pośrednich może pomóc w określeniu źródła niektórych narzędzi programistycznych w dołączonym do klas częściowych w skompilowanej aplikacji.  
  
 Programy obsługi zdarzeń w klasie pochodnej musi być `internal override` (`Friend Overrides` w [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) w celu zastąpienia klas zastępczych dla programów obsługi, jak utworzony w klasie pośrednie podczas kompilacji. W przeciwnym razie implementacji klasy pochodnej Ukryj (tle) implementacji klasa pośrednicząca i nie są wywoływane programy obsługi klasa pośrednicząca.  
  
 Podczas definiowania zarówno `x:Class` i `x:Subclass`, nie trzeba podać implementacji klasy, która odwołuje się do niego `x:Class`. Musisz podać jego nazwę przy użyciu `x:Class` atrybutu, dzięki czemu kompilator ma pewne wskazówki dotyczące klasy, która tworzy w plikach pośredniego (kompilator nie wybierz nazwę domyślną w tym przypadku). Można nadać `x:Class` klasa implementacji; mimo to nie jest typowym scenariuszem stosowania zarówno `x:Class` i `x:Subclass`.  
  
## <a name="see-also"></a>Zobacz też  
 [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md)  
 [XAML oraz klas niestandardowych dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)

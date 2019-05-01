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
ms.openlocfilehash: 850fe8acf9e47149bd385e78b30e04ba77d7a8b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938869"
---
# <a name="xsubclass-directive"></a>x:Subclass — dyrektywa
Modyfikuje zachowanie kompilacji znaczników XAML podczas `x:Class` jest również udostępniany. Zamiast tworzyć częściową klasą, która opiera się na `x:Class`, podane `x:Class` jest tworzona jako klasa pośrednicząca, i następnie powinien opierać się na podanej klasy pochodnej `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`namespace`|Opcjonalna. Określa przestrzeń nazw środowiska CLR, który zawiera `classname`. Jeśli `namespace` określono pojedynczego znaku kropki (.) oddziela `namespace` i `classname`.|  
|`classname`|Wymagana. Określa nazwę CLR częściową klasą, która łączy XAML załadowane i usługi związane z kodem dla tego XAML. Zobacz uwagi.|  
|`subclassNamespace`|Opcjonalna. Może być inny niż `namespace` Jeśli każdej przestrzeni nazw można rozwiązać drugi. Określa przestrzeń nazw środowiska CLR, który zawiera `subclassName`. Jeśli `subclassName` określono pojedynczego znaku kropki (.) oddziela `subclassNamespace` i `subclassName`.|  
|`subclassName`|Wymagana. Określa nazwę CLR podklasy.|  
  
## <a name="dependencies"></a>Zależności  
 [x: Class — dyrektywa](x-class-directive.md) również musi być podana dla tego samego obiektu, a ten obiekt musi być elementem głównym produkcji XAML.  
  
## <a name="remarks"></a>Uwagi  
 `x:Subclass` użycie jest przeznaczone głównie dla języków, które nie obsługują deklaracji klasy częściowej.  
  
 Klasa służy jako `x:Subclass` nie może być klasą zagnieżdżoną i `x:Subclass` musi odwoływać się do obiektu głównego, zgodnie z opisem w sekcji "Dependencies".  
  
 W przeciwnym razie koncepcyjny znaczenie `x:Subclass` jest niezdefiniowana przy wdrażaniu usług programu .NET Framework XAML. Jest to spowodowane zachowanie usług programu .NET Framework XAML nie określa ogólnym modelu programowania, XAML, które są połączone znaczników i kopii kodu. Implementacje dalsze pojęcia związane z `x:Class` i `x:Subclass` są wykonywane przez określonych platform, korzystające z modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML, skompilowany kod znaczników i na podstawie CLR związane z kodem. Każdej struktury, może mieć własne działania kompilacji, umożliwiające niektóre zachowania lub określonych składników, które muszą być zawarte w środowisku kompilacji. W ramach akcji kompilacji można też różnią się zależnie od określonego języka środowiska CLR, używany do związanym z kodem.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 `x:Subclass` można na głównej stronie lub <xref:System.Windows.Application> główny urząd certyfikacji w definicji aplikacji, która ma już `x:Class`. Deklarowanie `x:Subclass` dowolnego elementu innego niż katalog główny strony lub aplikacji lub określając jej w przypadku, gdy nie `x:Class` istnieje, powoduje błąd kompilacji.  
  
 Tworzenie pochodnej klasy pracę poprawnie na potrzeby `x:Subclass` scenariusz jest dosyć złożona. Może być konieczne zbadanie pośrednie pliki (pliki .g utworzony w folderze obj. projektu przez kompilacji znaczników, z nazwami, które zawierają nazwy plików .xaml). Te pliki pośrednie mogą pomóc w określeniu pochodzenia pewnych narzędzi programistycznych w dołączonym do klas częściowych w skompilowanej aplikacji.  
  
 Programy obsługi zdarzeń w klasie pochodnej musi być `internal override` (`Friend Overrides` programu Microsoft Visual Basic) w celu zastąpienia klas zastępczych dla programów obsługi, podczas tworzenia klasy pośrednie podczas kompilacji. W przeciwnym razie implementacji klasy pochodnej ukryć (w tle) Implementacja klasy pośrednich i nie są wywoływane programy obsługi klasa pośrednicząca.  
  
 Podczas definiowania obu `x:Class` i `x:Subclass`, trzeba podawać żadnych implementację klasy, która odwołuje się do niej `x:Class`. Musisz nadać mu nazwę, za pośrednictwem `x:Class` atrybutu, aby kompilator zawiera wskazówki dotyczące klasy, która tworzy w plikach pośredni (kompilator nie wybierać nazwę domyślną w tym przypadku). Możesz nadać `x:Class` Implementacja klasy; jednak nie jest to typowy scenariusz przy użyciu zarówno `x:Class` i `x:Subclass`.  
  
## <a name="see-also"></a>Zobacz także

- [x:Class, dyrektywa](x-class-directive.md)
- [Klasy XAML i niestandardowe dla WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)

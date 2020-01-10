---
title: Wybieranie między klasą i strukturą
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
ms.openlocfilehash: 34ab2589364e244fed1c64c1703205fb4b0832e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709520"
---
# <a name="choosing-between-class-and-struct"></a>Wybieranie między klasą i strukturą
Jedną z podstawowych decyzji projektowych każdej twarzy projektanta platformy jest to, czy projekt typu ma być klasą (typem referencyjnym) czy jako struktura (typ wartości). Dobre zrozumienie różnic w zachowaniu typów referencyjnych i typów wartości jest decydujące w przypadku dokonania tego wyboru.  
  
 Pierwszą różnicą między typami referencyjnymi i typami wartości, które należy wziąć pod uwagę, jest to, że typy odwołań są przydzielane na stercie i elementy bezużyteczne, a typy wartości są przydzielane na stosie lub w wierszu zawierającym typy i cofnięte przydział, gdy stos powoduje cofnięcie przydziału typu "niewietrzne" lub "typ zawierający". W związku z tym alokacje i cofanie alokacji typów wartości są ogólnie tańsze niż alokacje i cofanie alokacji typów referencyjnych.  
  
 Następnie tablice typów referencyjnych są przydzielane poza wierszem, co oznacza, że elementy tablicy są tylko odwołaniami do wystąpień typu referencyjnego znajdującego się na stercie. Tablice typu wartości są przypisywane wewnętrznie, co oznacza, że elementy tablicy są rzeczywistymi wystąpieniami typu wartości. W związku z tym alokacje i cofanie alokacji tablic typu wartości są znacznie tańsze niż alokacje i cofanie alokacji tablic typu referencyjnego. Ponadto, w większości przypadków tablice typów wartości wykazują znacznie lepszą miejscowość odwołania.  
  
 Kolejna różnica jest związana z użyciem pamięci. Typy wartości są zapakowane, gdy rzutowanie na typ referencyjny lub jeden z implementowanych interfejsów. Są one nieopakowane podczas rzutowania z powrotem na typ wartości. Ponieważ pola są obiektami przydzielonymi na stercie i są zbierane jako elementy bezużyteczne, zbyt dużo opakowania i rozpakowywanie mogą mieć negatywny wpływ na stertę, Moduł wyrzucania elementów bezużytecznych i ostatecznie wydajność aplikacji.  W przeciwieństwie do tego opakowanie nie występuje w przypadku rzutowania typów referencyjnych. (Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](../../csharp/programming-guide/types/boxing-and-unboxing.md)).
  
 Następnie przydziały typu odwołania kopiują odwołanie, podczas gdy przydziały typów wartości skopiują całą wartość. W związku z tym przypisania dużych typów referencyjnych są tańsze niż przydziały dużych typów wartości.  
  
 Na koniec typy odwołań są przesyłane przez odwołanie, a typy wartości są przenoszone przez wartość. Zmiany w wystąpieniu typu odwołania wpływają na wszystkie odwołania wskazujące na to wystąpienie. Wystąpienia typu wartości są kopiowane, gdy są przesyłane przez wartość. W przypadku zmiany wystąpienia typu wartości kurs nie ma wpływu na żadne kopie. Ponieważ kopie nie są tworzone jawnie przez użytkownika, ale są niejawnie tworzone, gdy argumenty są przekazane lub zwracane są wartości zwracanych, typy wartości, które mogą zostać zmienione, mogą być mylące dla wielu użytkowników. W związku z tym typy wartości powinny być niezmienne.  
  
 Jako reguła kciuka większość typów w środowisku powinna być klasą. Istnieją jednak sytuacje, w których cechy typu wartości są bardziej odpowiednie do używania struktur.  
  
 **✓ CONSIDER** definiowania struktury zamiast klasy, jeśli wystąpienia typu małych i często krótkim okresie lub często są osadzone w innych obiektach.  
  
 **X AVOID** definiowania struktury, chyba że typ ma wszystkie następujące właściwości:  
  
- Logicznie reprezentuje pojedynczą wartość, podobną do typów pierwotnych (`int`, `double`itp.).  
  
- Ma rozmiar wystąpienia poniżej 16 bajtów.  
  
- Jest to niezmienne.  
  
- Nie musi być on często opakowany.  
  
 We wszystkich innych przypadkach należy zdefiniować typy jako klasy.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)

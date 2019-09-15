---
title: Modyfikatory dostępu — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: b415bf143e7da46b3ecd2c0828a3f8151878435a
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971678"
---
# <a name="access-modifiers-c-programming-guide"></a>Modyfikatory dostępu (Przewodnik programowania w języku C#)
Wszystkie typy i elementy członkowskie typu mają poziom dostępności, który kontroluje, czy mogą być używane z innego kodu w zestawie lub w innych zestawach. Można użyć następujących modyfikatorów dostępu, aby określić dostępność typu lub elementu członkowskiego podczas deklarowania:  
  
 [public](../../language-reference/keywords/public.md)  
 Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego innego kodu w tym samym zestawie lub innym zestawie, który odwołuje się do niego. 
  
 [private](../../language-reference/keywords/private.md)  
 Typ lub element członkowski można uzyskać dostęp tylko do kodu w tej samej klasie lub strukturze.  
  
 [protected](../../language-reference/keywords/protected.md)  
 Typ lub element członkowski można uzyskać dostęp tylko do kodu w tej samej klasie lub w klasie, która jest pochodną tej klasy.  
 [internal](../../language-reference/keywords/internal.md)  
 Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.  
  
 [chroniona wewnętrzna](../../language-reference/keywords/protected-internal.md) Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w zestawie, w którym jest zadeklarowany, lub z klasy pochodnej w innym zestawie. 

 [prywatne chronione](../../language-reference/keywords/private-protected.md) Typ lub element członkowski jest dostępny tylko w obrębie swojego zestawu deklarującego przez kod w tej samej klasie lub w typie, który jest pochodną tej klasy.
  
 W poniższych przykładach pokazano, jak określić Modyfikatory dostępu dla typu i składowej:  
  
 [!code-csharp[csProgGuideObjects#72](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#72)]  
  
 Nie wszystkie Modyfikatory dostępu mogą być używane przez wszystkie typy lub elementy członkowskie we wszystkich kontekstach, a w niektórych przypadkach dostępność elementu członkowskiego typu jest ograniczona przez dostępność typu zawierającego. Poniższe sekcje zawierają więcej informacji na temat ułatwień dostępu.  
  
## <a name="class-and-struct-accessibility"></a>Ułatwienia dostępu klasy i struktury  
 Klasy i struktury, które są zadeklarowane bezpośrednio w przestrzeni nazw (innymi słowy, które nie są zagnieżdżone w innych klasach lub strukturach) mogą być publiczne lub wewnętrzne. Wewnętrzna jest wartością domyślną, jeśli nie określono modyfikatora dostępu.  
  
 Elementy członkowskie struktury, w tym zagnieżdżone klasy i struktury, mogą być deklarowane jako publiczne, wewnętrzne lub prywatne. Elementy członkowskie klasy, w tym zagnieżdżone klasy i struktury, mogą być publiczne, chronione wewnętrznie, chronione, wewnętrzne, prywatne i prywatne. Poziom dostępu dla elementów członkowskich klasy i elementów członkowskich struktury, w tym zagnieżdżonych klas i struktur, jest domyślnie prywatny. Prywatne typy zagnieżdżone nie są dostępne spoza typu zawierającego.  
  
 Klasy pochodne nie mogą mieć większej dostępności niż ich typy podstawowe. Innymi słowy, nie można mieć klasy `B` publicznej, która pochodzi od klasy `A`wewnętrznej. Jeśli jest to dozwolone, miałoby to wpływ `A` na publiczną, ponieważ wszystkie chronione lub wewnętrzne `A` elementy członkowskie są dostępne z klasy pochodnej.  
  
 Można włączyć określone inne zestawy, aby uzyskać dostęp do typów wewnętrznych przy użyciu InternalsVisibleToAttribute. Aby uzyskać więcej informacji, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).  
  
## <a name="class-and-struct-member-accessibility"></a>Ułatwienia dostępu do elementów członkowskich klasy i struktury  
 Elementy członkowskie klasy (w tym zagnieżdżone klasy i struktury) mogą być deklarowane przy użyciu dowolnego z sześciu typów dostępu. Elementy członkowskie struktury nie mogą być deklarowane jako chronione, ponieważ struktury nie obsługują dziedziczenia.  
  
 Zwykle dostępność elementu członkowskiego nie jest większa niż dostępność typu, który go zawiera. Jednak publiczna składowa klasy wewnętrznej może być dostępna spoza zestawu, jeśli element członkowski implementuje metody interfejsu lub przesłania metody wirtualne, które są zdefiniowane w publicznej klasie bazowej.  
  
 Typ dowolnego elementu członkowskiego, który jest polem, właściwością lub zdarzeniem, musi być co najmniej tak samo samo jak element członkowski. Analogicznie, typ zwracany i typy parametrów dowolnego elementu członkowskiego, który jest metody, indeksatora lub delegata, muszą być co najmniej tak samo samo jak element członkowski. Na przykład nie można mieć metody `M` publicznej, która zwraca klasę `C` , chyba że `C` jest również publiczna. Analogicznie, nie można mieć chronionej właściwości typu `A` , `A` jeśli jest zadeklarowana jako prywatna.  
  
 Operatory zdefiniowane przez użytkownika muszą być zawsze deklarowane jako publiczne i statyczne. Aby uzyskać więcej informacji, zobacz przeciążanie [operatora](../../language-reference/operators/operator-overloading.md).  
  
 Finalizatory nie mogą mieć modyfikatorów dostępności.  
  
 Aby ustawić poziom dostępu dla elementu członkowskiego klasy lub struktury, Dodaj odpowiednie słowo kluczowe do deklaracji elementu członkowskiego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideObjects#73](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#73)]  
  
> [!NOTE]
> Chroniony wewnętrzny poziom dostępności oznacza ochronę lub wewnętrzne, niechronione i wewnętrzne. Innymi słowy, dostęp do chronionej wewnętrznej składowej można uzyskać z dowolnej klasy w tym samym zestawie, łącznie z klasami pochodnymi. Aby ograniczyć dostępność tylko do klas pochodnych w tym samym zestawie, zadeklaruj samą klasę jako wewnętrzną i Zadeklaruj jej składowe jako chronione. Ponadto, począwszy od C# 7,2, można użyć modyfikatora Private Protected Access, aby osiągnąć ten sam wynik bez konieczności wypełniania klasy zawierającej.  
  
## <a name="other-types"></a>Inne typy  
 Interfejsy zadeklarowane bezpośrednio w przestrzeni nazw mogą być deklarowane jako publiczne lub wewnętrzne, podobnie jak klasy i struktury, interfejsy domyślnie mają dostęp wewnętrzny. Elementy członkowskie interfejsu są zawsze publiczne, ponieważ celem interfejsu jest umożliwienie innym typom dostępu do klasy lub struktury. Nie można zastosować modyfikatorów dostępu do elementów członkowskich interfejsu.  
  
 Elementy członkowskie wyliczenia są zawsze publiczne i nie można zastosować modyfikatorów dostępu.  
  
 Delegaty zachowują się jak klasy i struktury. Domyślnie mają oni dostęp wewnętrzny po zadeklarowaniu bezpośrednio w przestrzeni nazw i prywatnym dostępie w przypadku zagnieżdżenia.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Interfejsy](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
- [interface](../../language-reference/keywords/interface.md)

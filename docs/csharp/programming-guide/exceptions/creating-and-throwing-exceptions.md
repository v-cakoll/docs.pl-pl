---
title: Tworzenie i zgłaszanie wyjątków — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: f775a0917560a219f24329adcb1542f605d47dc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712302"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Tworzenie i zgłaszanie wyjątków (Przewodnik programowania w języku C#)
Wyjątki są używane do wskazania, że wystąpił błąd podczas uruchamiania programu. Obiekty wyjątku, które opisują błąd są tworzone, a następnie *generowane* za pomocą [throw](../../language-reference/keywords/throw.md) słowa kluczowego. Następnie środowiska uruchomieniowego wyszukuje najbardziej zgodny program obsługi wyjątków.  
  
 Programiści powinni zgłaszać wyjątki, gdy spełniony jest co najmniej jeden z następujących warunków:  
  
- Metoda nie może ukończyć jej zdefiniowanej funkcjonalności.  
  
     Na przykład jeśli parametr do metody ma nieprawidłową wartość:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- Nieodpowiednie wywołanie obiektu jest na podstawie stanu obiektu.  
  
     Jednym z przykładów może być próba zapisu do pliku tylko do odczytu. W przypadkach, gdy stan obiektu nie zezwala na <xref:System.InvalidOperationException> operację, należy zgłosić wystąpienie lub obiekt na podstawie wyprowadzenia tej klasy. Jest to przykład metody, która <xref:System.InvalidOperationException> zgłasza obiekt:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Gdy argument do metody powoduje wyjątek.  
  
     W takim przypadku należy przechwycić oryginalny wyjątek i utworzyć wystąpienie. <xref:System.ArgumentException> Oryginalny wyjątek powinny być przekazywane do <xref:System.ArgumentException> konstruktora jako <xref:System.Exception.InnerException%2A> parametr:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Wyjątki zawierają właściwość <xref:System.Exception.StackTrace%2A>o nazwie . Ten ciąg zawiera nazwę metod na bieżącym stosie wywołań, wraz z nazwą pliku i numerem wiersza, w którym został zgłoszony wyjątek dla każdej metody. Obiekt <xref:System.Exception.StackTrace%2A> jest tworzony automatycznie przez program runtime języka wspólnego (CLR) z punktu `throw` instrukcji, tak aby wyjątki muszą być generowane od punktu, w którym powinien rozpocząć się śledzenie stosu.  
  
 Wszystkie wyjątki zawierają <xref:System.Exception.Message%2A>właściwość o nazwie . Ten ciąg powinien być ustawiony, aby wyjaśnić przyczynę wyjątku. Należy zauważyć, że informacje, które są wrażliwe na zabezpieczenia nie powinny być umieszczane w tekście wiadomości. Oprócz <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> zawiera właściwość <xref:System.ArgumentException.ParamName%2A> o nazwie, która powinna być ustawiona na nazwę argumentu, który spowodował wyjątek wyjątek. W przypadku ustawiania właściwości <xref:System.ArgumentException.ParamName%2A> należy ustawić `value`na wartość .  
  
 Metody publiczne i chronione należy zgłaszać wyjątki, gdy nie można ukończyć ich zamierzonych funkcji. Klasa wyjątku, który jest generowany powinien być najbardziej szczegółowy wyjątek dostępny, który pasuje do warunków błędu. Wyjątki te powinny być udokumentowane jako część funkcji klasy i pochodne klasy lub aktualizacje do oryginalnej klasy powinny zachować to samo zachowanie dla zgodności z poprzednimi wersjami.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Czego należy unikać podczas wyrzucania wyjątków  
 Poniższa lista identyfikuje praktyki, których należy unikać podczas zgłaszania wyjątków:  
  
- Wyjątki nie powinny być używane do zmiany przepływu programu w ramach zwykłego wykonywania. Wyjątki powinny być używane tylko do zgłaszania i obsługi warunków błędu.  
  
- Wyjątki nie powinny być zwracane jako wartość zwracana lub parametr, a nie generowane.  
  
- Nie <xref:System.Exception?displayProperty=nameWithType>wyrzucaj <xref:System.SystemException?displayProperty=nameWithType> <xref:System.NullReferenceException?displayProperty=nameWithType>, <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> , lub celowo z własnego kodu źródłowego.  
  
- Nie należy tworzyć wyjątków, które mogą być generowane w trybie debugowania, ale nie w trybie zwalniania. Aby zidentyfikować błędy w czasie wykonywania podczas fazy opracowywania, należy użyć DebugAssert zamiast tego.  
  
## <a name="defining-exception-classes"></a>Definiowanie klas wyjątków  
 Programy mogą zgłaszać wstępnie zdefiniowaną <xref:System> klasę wyjątków w obszarze nazw (z wyjątkiem przypadków <xref:System.Exception>wcześniej odnotowanych) lub tworzyć własne klasy wyjątków, wywodząc się z . Klasy pochodne należy zdefiniować co najmniej cztery konstruktory: jeden konstruktor bezparametrów, <xref:System.Exception.Message%2A> jeden, który ustawia właściwość komunikatu i jeden, który ustawia zarówno i <xref:System.Exception.InnerException%2A> właściwości. Czwarty konstruktor służy do serializacji wyjątku. Nowe klasy wyjątków powinny być serializowane. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Nowe właściwości należy dodać do klasy wyjątków tylko wtedy, gdy dane, które dostarczają jest przydatne do rozpoznawania wyjątku. Jeśli nowe właściwości są dodawane do klasy `ToString()` wyjątków pochodnych, powinny zostać zastąpione w celu zwrócenia dodanych informacji.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) i [throw instrukcji](~/_csharplang/spec/statements.md#the-throw-statement) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Hierarchia wyjątków](../../../standard/exceptions/index.md)
- [Obsługa wyjątków](./exception-handling.md)

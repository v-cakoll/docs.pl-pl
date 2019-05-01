---
title: Obiekty rozszerzalne
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: 1af44f2394bbf27f9219831612b4e73d7a1759e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857886"
---
# <a name="extensible-objects"></a>Obiekty rozszerzalne

Wzorzec extensible object jest używany, albo rozszerzanie istniejących klas środowiska uruchomieniowego przy użyciu nowych funkcji lub dodanie nowego Państwa do obiektu. Rozszerzenia, dołączony do jednego z obiekty rozszerzalne umożliwiają zachowania w bardzo różnych etapach przetwarzania dostęp do udostępnionego stanu i dołączony do obiektu extensible wspólnego, które mogą uzyskiwać dostęp do funkcji.

## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject\<T > wzorzec

Istnieją trzy interfejsy we wzorcu extensible object: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, i <xref:System.ServiceModel.IExtensionCollection%601>.

<xref:System.ServiceModel.IExtensibleObject%601> Interfejs jest implementowany przez typy, które umożliwiają <xref:System.ServiceModel.IExtension%601> obiektów, aby dostosować ich funkcje.

Obiekty rozszerzalne Zezwalaj na agregację dynamiczne <xref:System.ServiceModel.IExtension%601> obiektów. <xref:System.ServiceModel.IExtension%601> obiekty charakteryzują się następujący interfejs:

```csharp
public interface IExtension<T>
where T : IExtensibleObject<T>
{
    void Attach(T owner);
    void Detach(T owner);
}
```

Ograniczenie typu gwarantuje, że rozszerzenia mogą być definiowane tylko dla klas, które są <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A> powiadomienie agregacji lub podziału.

Jest on prawidłowy dla implementacji w celu ograniczenia podczas ich mogą być dodawane lub usuwane z właścicielem. Na przykład można uniemożliwić usunięcie całkowicie, nie można przydzielać dodawania lub usuwania rozszerzenia, gdy właściciel lub rozszerzenia są w stanie nie zezwalaj na dodawanie wielu właścicielom jednocześnie lub zezwolić tylko pojedynczego dodawania następuje usunięcie jednego.

<xref:System.ServiceModel.IExtension%601> nie oznacza wszystkie interakcje z innych standardowych interfejsów zarządzanych. W szczególności <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metody na obiekt właściciela zwykle nie odłączyć jego rozszerzenia.

Gdy rozszerzenie zostanie dodany do kolekcji, <xref:System.ServiceModel.IExtension%601.Attach%2A> jest wywoływana przed przejdzie do kolekcji. Gdy rozszerzenie zostanie usunięty z kolekcji, <xref:System.ServiceModel.IExtension%601.Detach%2A> jest wywoływana po jego usunięciu. (Przy założeniu synchronizacji odpowiednich) oznacza, że rozszerzenie liczyć na dostępne tylko w kolekcji, gdy jest to między <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A>.

Przekazany obiekt <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> lub <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> nie muszą być <xref:System.ServiceModel.IExtension%601> (na przykład, możesz przekazać dowolny obiekt), ale rozszerzenie zwracany jest <xref:System.ServiceModel.IExtension%601>.

Jeśli jest bez rozszerzenia w kolekcji <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> zwraca wartość null, i <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> zwraca pustą kolekcję. Jeśli zaimplementować wiele rozszerzeń <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> zwraca jeden z nich. Wartość zwracana z <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> jest migawką.

Istnieją dwa główne scenariusze. Pierwszy scenariusz używa <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> właściwości jako słownik na podstawie typu, aby wstawić stanu na obiekcie, aby umożliwić inny składnik w celu wyszukania go przy użyciu typu.

Drugi scenariusz używa <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A> właściwości, aby włączyć obiekt do wzięcia udziału w zachowanie niestandardowe, takie jak rejestrowanie zdarzeń, oglądając stanami i tak dalej.

<xref:System.ServiceModel.IExtensionCollection%601> Interfejsu jest kolekcją <xref:System.ServiceModel.IExtension%601> obiekty, które umożliwiają pobieranie <xref:System.ServiceModel.IExtension%601> według ich typu. <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> Zwraca ostatnio dodany obiekt, który jest <xref:System.ServiceModel.IExtension%601> tego typu.

### <a name="extensible-objects-in-windows-communication-foundation"></a>Obiekty rozszerzalne w Windows Communication Foundation

Istnieją cztery obiekty rozszerzalne w Windows Communication Foundation (WCF):

- <xref:System.ServiceModel.ServiceHostBase> — To jest klasa bazowa dla hosta usługi.  Rozszerzenia tej klasy może służyć do rozszerzania działania <xref:System.ServiceModel.ServiceHostBase> sam lub do przechowywania stanu dla każdej usługi.

- <xref:System.ServiceModel.InstanceContext> — Ta klasa łączy wystąpienia typu usługi ze środowiskiem uruchomieniowym usługi.  Zawiera informacje o wystąpieniu, a także odwołania do <xref:System.ServiceModel.InstanceContext>zawierające <xref:System.ServiceModel.ServiceHostBase>. Rozszerzenia tej klasy może służyć do rozszerzania działania <xref:System.ServiceModel.InstanceContext> lub do przechowywania stanu dla każdej usługi.

- <xref:System.ServiceModel.OperationContext> — Ta klasa przedstawia informacje o operacji, środowisko uruchomieniowe zbierające dla każdej operacji.  Obejmuje to informacje, takie jak nagłówki wiadomości przychodzących, właściwości wiadomości przychodzących, przychodzącej tożsamości zabezpieczeń i inne informacje.  Rozszerzenia tej klasy można wydłużyć zachowanie <xref:System.ServiceModel.OperationContext> ani do przechowywania stanu dla każdej operacji.

- <xref:System.ServiceModel.IContextChannel> — Ten interfejs umożliwia inspekcję każdy stan dla kanałów i serwery proxy utworzone przez środowisko wykonawcze programu WCF.  Rozszerzenia tej klasy można wydłużyć zachowanie <xref:System.ServiceModel.IClientChannel> lub można użyć do przechowywania stanu dla każdego kanału.

W poniższym przykładzie kodu pokazano sposób użycia proste rozszerzenie, aby śledzić <xref:System.ServiceModel.InstanceContext> obiektów.

[!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>

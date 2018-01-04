---
title: Obiekty rozszerzalne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7d7b5245130a7581efbf9badb0699f57a6743dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extensible-objects"></a>Obiekty rozszerzalne
Wzorzec rozszerzonego obiektu jest używany, aby wydłużyć istniejące klasy środowiska uruchomieniowego z nowych funkcji lub aby dodać nowy stan do obiektu. Dołączony do jednego z obiekty rozszerzalne, dzięki rozszerzeniom zachowania w bardzo różnych etapach przetwarzania dostęp do stanu udostępnionego i dołączony do obiektu extensible wspólnej mogą uzyskiwać dostęp do funkcji.  
  
## <a name="the-iextensibleobjectt-pattern"></a>Interfejs IExtensibleObject\<T > wzorca  
 Istnieją trzy interfejsy we wzorcu obiektu extensible: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, i <xref:System.ServiceModel.IExtensionCollection%601>.  
  
 <xref:System.ServiceModel.IExtensibleObject%601> Interfejs jest implementowany przez typy, które umożliwiają <xref:System.ServiceModel.IExtension%601> obiektów, aby dostosować ich funkcje.  
  
 Obiekty rozszerzalne Zezwalaj na agregację dynamiczne <xref:System.ServiceModel.IExtension%601> obiektów. <xref:System.ServiceModel.IExtension%601>obiekty charakteryzują się interfejsu:  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 Ograniczenie typu gwarantuje, że rozszerzenia można zdefiniować tylko dla klas, które są <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A>i <xref:System.ServiceModel.IExtension%601.Detach%2A> powiadamiać agregacji lub podziału.  
  
 Jest on prawidłowy dla implementacji ograniczyć, gdy mogą być dodawane i usuwane z użyciem właściciela. Na przykład można uniemożliwić usunięcie całkowicie, brak zezwolenia Dodawanie lub usuwanie rozszerzeń, gdy właściciel lub rozszerzenia są w stanie nie zezwalaj na dodawanie jednocześnie do wielu właścicieli lub Zezwalaj tylko jednego dodanie następuje pojedynczego Usuń.  
  
 <xref:System.ServiceModel.IExtension%601>nie oznacza wszystkie interakcje z innych standardowych interfejsów zarządzanych. W szczególności <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metody dla obiekt właściciela zwykle nie odłączyć jej rozszerzeń.  
  
 Jeśli rozszerzenie zostanie dodane do kolekcji, <xref:System.ServiceModel.IExtension%601.Attach%2A> jest wywoływana przed przechodzi on w kolekcji. Rozszerzenie zostanie usunięty z kolekcji, <xref:System.ServiceModel.IExtension%601.Detach%2A> jest wywoływana po jego usunięciu. (Przy założeniu odpowiedniej synchronizacji) oznacza, że rozszerzenie liczyć na dostępne tylko w kolekcji w czasie, gdy jest między <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A>.  
  
 Obiekt przekazywany do <xref:System.ServiceModel.IExtensionCollection%601.FindAll%60%601%2A> lub <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A> nie muszą być <xref:System.ServiceModel.IExtension%601> (na przykład można przekazać dowolnych obiektów), ale zwrócone rozszerzenie to <xref:System.ServiceModel.IExtension%601>.  
  
 Jeśli jest bez rozszerzenia w kolekcji <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A> zwraca wartość null, a <xref:System.ServiceModel.IExtensionCollection%601.FindAll%60%601%2A> zwraca pustą kolekcję. Jeśli implementuje wiele rozszerzeń <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A> zwraca jeden z nich. Wartość zwracana z <xref:System.ServiceModel.IExtensionCollection%601.FindAll%60%601%2A> jest to migawka.  
  
 Istnieją dwa główne scenariusze. Używa pierwszego scenariusza <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> właściwość jako słownik na podstawie typu do wstawienia stanu na obiekt, aby włączyć inny składnik do wyszukania go przy użyciu typu.  
  
 Drugi scenariusz używa <xref:System.ServiceModel.IExtension%601.Attach%2A> i <xref:System.ServiceModel.IExtension%601.Detach%2A> właściwości, aby włączyć obiekt, aby uczestniczyć w zachowaniu niestandardowe, takie jak rejestrowanie zdarzeń, obserwowanie przejść stanu i tak dalej.  
  
 <xref:System.ServiceModel.IExtensionCollection%601> Interfejsu jest kolekcją <xref:System.ServiceModel.IExtension%601> obiektów, które umożliwiają pobieranie <xref:System.ServiceModel.IExtension%601> przez jego typu. <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A?displayProperty=nameWithType>Zwraca ostatnio dodany obiekt, który jest <xref:System.ServiceModel.IExtension%601> tego typu.  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Obiekty rozszerzalne programu Windows Communication Foundation  
 Istnieją cztery obiekty rozszerzalne w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]:  
  
-   <xref:System.ServiceModel.ServiceHostBase>— To jest klasa podstawowa dla hosta usługi.  Rozszerzenia tej klasy można rozszerzyć zachowanie <xref:System.ServiceModel.ServiceHostBase> samego lub do przechowywania stanu dla każdej usługi.  
  
-   <xref:System.ServiceModel.InstanceContext>— Ta klasa wystąpienia typu usługi łączy się z usługą środowiska uruchomieniowego usługi.  Zawiera on informacje dotyczące tego wystąpienia, a także odwołanie do <xref:System.ServiceModel.InstanceContext>zawierającego <xref:System.ServiceModel.ServiceHostBase>. Rozszerzenia tej klasy można rozszerzyć zachowanie <xref:System.ServiceModel.InstanceContext> lub do przechowywania stanu dla każdej usługi.  
  
-   <xref:System.ServiceModel.OperationContext>— Ta klasa reprezentuje informacje operacji zbierające środowiska uruchomieniowego dla każdej operacji.  Dotyczy to również informacje, takie jak nagłówki wiadomości przychodzących, właściwości przychodzących wiadomości przychodzącej tożsamości zabezpieczeń i inne informacje.  Rozszerzenia tej klasy można wydłużyć zachowanie <xref:System.ServiceModel.OperationContext> ani do przechowywania stanu dla każdej operacji.  
  
-   <xref:System.ServiceModel.IContextChannel>— Ten interfejs umożliwia inspekcji każdy stan dla kanałów i serwery proxy utworzony przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska wykonawczego.  Rozszerzenia tej klasy można wydłużyć zachowanie <xref:System.ServiceModel.IClientChannel> lub służy do przechowywania stanu dla poszczególnych kanałów.  
  
-  
  
 W poniższym przykładzie pokazano sposób użycia prostego rozszerzenia do śledzenia <xref:System.ServiceModel.InstanceContext> obiektów.  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.IExtensibleObject%601>  
 <xref:System.ServiceModel.IExtension%601>  
 <xref:System.ServiceModel.IExtensionCollection%601>

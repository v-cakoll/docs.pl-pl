---
title: Najlepsze rozwiązania dotyczące częściowego zaufania
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: c83c36020cfd5b41e99ff9eeb7968d0b5df909a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184083"
---
# <a name="partial-trust-best-practices"></a>Najlepsze rozwiązania dotyczące częściowego zaufania
W tym temacie opisano najlepsze rozwiązania, podczas uruchamiania usługi Windows Communication Foundation (WCF) w środowisku częściowej relacji zaufania.  
  
## <a name="serialization"></a>Serializacja  
 Zastosuj następujące rozwiązania, korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> w częściowo zaufanych aplikacji.  
  
-   Wszystkie możliwe do serializacji typy muszą być jawnie oznaczone `[DataContract]` atrybutu. Następujące techniki nie są obsługiwane w środowisku częściowej relacji zaufania:  
  
-   Oznaczanie klasy, aby można było serializować ją przy <xref:System.SerializableAttribute>.  
  
-   Implementowanie <xref:System.Runtime.Serialization.ISerializable> interfejs umożliwia klasy do kontrolowania procesu serializacji.  
  
### <a name="using-datacontractserializer"></a>Przy użyciu elementu DataContractSerializer  
  
-   Wszystkie typy oznaczone `[DataContract]` atrybutu muszą być publiczne. Nie można zserializować niepubliczne typy w środowisku częściowej relacji zaufania.  
  
-   Wszystkie `[DataContract]` elementów członkowskich w serializacji `[DataContract]` typu muszą być publiczne. Typu z niepublicznymi `[DataMember]` nie może być serializowana w środowisku częściowej relacji zaufania.  
  
-   Metody obsługi zdarzeń serializacji (takie jak `OnSerializing`, `OnSerialized`, `OnDeserializing`, i `OnDeserialized`) musi być zadeklarowany jako publiczny. Jednak zarówno jawne i niejawne implementacje <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> są obsługiwane.  
  
-   `[DataContract]` typy zaimplementowane w zestawach oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nie musi wykonywać akcje związane z zabezpieczeniami w Konstruktorze typu jako <xref:System.Runtime.Serialization.DataContractSerializer> nie wywołuje konstruktora obiektu nowo tworzone podczas deserializacji. W szczególności należy unikać następujące typowe metody zabezpieczeń dla `[DataContract]` typów:  
  
-   Podjęto próbę ograniczyć dostęp częściowej relacji zaufania, dzięki czemu konstruktora typu wewnętrznego lub prywatnego.  
  
-   Ograniczanie dostępu do typu, dodając `[LinkDemand]` do konstruktora typu.  
  
-   Przy założeniu, że ponieważ obiekt został pomyślnie utworzony, wszelkie sprawdzanie poprawności wymuszane przez Konstruktor ma zakończyło się pomyślnie.  
  
### <a name="using-ixmlserializable"></a>Za pomocą interfejsu IXmlSerializable  
 Zastosuj poniższe najlepsze rozwiązania, dla typów, które implementują <xref:System.Xml.Serialization.IXmlSerializable> i są serializowane, za pomocą <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
-   <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> Implementacje metod statycznych musi być `public`.  
  
-   Metody wystąpienia, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs musi być `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Przy użyciu usługi WCF z kodu platformy w pełni zaufany, który umożliwia wywołania z częściowo zaufanych obiektów wywołujących  
 Model zabezpieczeń częściowej relacji zaufania WCF przyjęto założenie, że dowolny obiekt wywołujący metodę publiczną WCF lub właściwości jest uruchomiona w kontekście zabezpieczeń (CAS) dostęp do kodu aplikacji macierzystej. Usługi WCF założono również, tej aplikacji tylko jeden kontekst zabezpieczeń nie istnieje dla każdego <xref:System.AppDomain>, i że w tym kontekście są ustawiane w <xref:System.AppDomain> czas utworzenia przez zaufanego hosta (na przykład przez wywołanie <xref:System.AppDomain.CreateDomain%2A> lub przez Menedżera aplikacji platformy ASP.NET).  
  
 Ten model zabezpieczeń ma zastosowanie do aplikacji z napisany przez użytkownika, które nie assert dodatkowe uprawnienia urzędów certyfikacji, na przykład kod użytkownika, działające w aplikacji ASP.NET zaufania średniej. Jednak kod platformy w pełni zaufane (na przykład firm zestaw, który jest zainstalowany w globalnej pamięci podręcznej i akceptuje wywołania z częściowo zaufanego kodu) należy wykonać opieki jawne wywołanie do usługi WCF w imieniu częściowo zaufanych aplikacji należy unikać Przedstawiamy luk w zabezpieczeniach na poziomie aplikacji.  
  
 Pełni zaufany kod, należy unikać zmieniania zestaw uprawnień CAS bieżącego wątku (przez wywołanie metody <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, lub <xref:System.Security.PermissionSet.Deny%2A>) przed wywoływania interfejsów API usługi WCF w imieniu częściowo zaufany kod. Potwierdzanie, odmawianie lub w przeciwnym razie tworzenie kontekstu uprawnień właściwych dla wątku, który jest niezależny od kontekstu zabezpieczeń na poziomie aplikacji może spowodować nieoczekiwane zachowanie. W zależności od aplikacji to zachowanie może spowodować powstanie luk w zabezpieczeniach na poziomie aplikacji.  
  
 Kod, który wywołania do programu WCF za pomocą kontekstu uprawnienia właściwe dla wątków musi być przygotowana do obsługi w następujących sytuacjach, które mogą wystąpić:  
  
-   Kontekst zabezpieczeń właściwe dla wątków może się nie powieść w czasie trwania operacji, która powoduje potencjalne wyjątki zabezpieczeń.  
  
-   Wewnętrzny kod usługi WCF, jak również wszelkie wywołania zwrotne dostarczone przez użytkownika może działać w kontekście zabezpieczeń innego niż ten, w którym pierwotnie zostało zainicjowane wywołanie. Konteksty te obejmują:  
  
    -   Kontekst uprawnień aplikacji.  
  
    -   Wszystkich kontekstach uprawnienia właściwe dla wątków, wcześniej utworzone przez inne wątki użytkownika używane do wywołania do usługi WCF w okresie istnienia aktualnie uruchomionych <xref:System.AppDomain>.  
  
 Usługi WCF gwarantuje częściowo zaufany kod nie może uzyskać uprawnienia pełnego zaufania, o ile takie uprawnienia są oceniane pod przez składnik przed wywołaniem do publicznych interfejsów API usługi WCF w pełni zaufane. Jednak go nie gwarantuje, że efekty potwierdzające pełnego zaufania jest izolowane do określonego wątku, operacji lub akcji przez użytkownika.  
  
 Najlepszym rozwiązaniem należy unikać tworzenia kontekstu uprawnienia właściwe dla wątków, wywołując <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, lub <xref:System.Security.PermissionSet.Deny%2A>. Zamiast tego należy udzielić lub odmówić uprawnień do aplikacji, tak aby nie <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, lub <xref:System.Security.PermissionSet.PermitOnly%2A> jest wymagana.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>

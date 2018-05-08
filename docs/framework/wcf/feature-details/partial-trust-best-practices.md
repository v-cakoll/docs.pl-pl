---
title: Najlepsze rozwiązania dotyczące częściowego zaufania
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: fca975ff4216384b970535273511eb07cd6ded68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="partial-trust-best-practices"></a>Najlepsze rozwiązania dotyczące częściowego zaufania
W tym temacie opisano najważniejsze wskazówki podczas uruchamiania usługi Windows Communication Foundation (WCF) w środowisku częściowej relacji zaufania.  
  
## <a name="serialization"></a>Serializacja  
 Zastosuj następujące rozwiązania, korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> w częściowo zaufanych aplikacji.  
  
-   Wszystkie typy serializacji musi być jawnie oznaczone `[DataContract]` atrybutu. Następujące techniki nie są obsługiwane w środowisku częściowej relacji zaufania:  
  
-   Oznaczenie klasy, aby można było serializować ją przy <xref:System.SerializableAttribute>.  
  
-   Implementowanie <xref:System.Runtime.Serialization.ISerializable> interfejs umożliwia klasę, aby kontrolować procesu serializacji.  
  
### <a name="using-datacontractserializer"></a>Przy użyciu elementu DataContractSerializer  
  
-   Wszystkie typy oznaczone `[DataContract]` atrybutu muszą być publiczne. Nie można zserializować typu niepubliczne w środowisku częściowej relacji zaufania.  
  
-   Wszystkie `[DataContract]` elementów członkowskich w serializacji `[DataContract]` typu muszą być publiczne. Typ z niepublicznych `[DataMember]` nie może być serializowany w środowisku częściowej relacji zaufania.  
  
-   Metody obsługi zdarzeń serializacji (takich jak `OnSerializing`, `OnSerialized`, `OnDeserializing`, i `OnDeserialized`) musi być zadeklarowany jako publiczny. Jednak zarówno bezpośrednie i pośrednie implementacje <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> są obsługiwane.  
  
-   `[DataContract]` typy zaimplementowana w zestawach oznaczonych <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nie należy wykonać czynności związane z zabezpieczeniami w Konstruktorze typu jako <xref:System.Runtime.Serialization.DataContractSerializer> nie wywołuje konstruktor obiektu nowo utworzone podczas deserializacji. W szczególności należy unikać następujące typowe techniki zabezpieczeń dla `[DataContract]` typów:  
  
-   Próba ograniczyć dostęp częściowej relacji zaufania, wprowadzając konstruktora typu wewnętrznego lub prywatnego.  
  
-   Ograniczanie dostępu do typu, dodając `[LinkDemand]` do konstruktora typu.  
  
-   Przy założeniu, że ponieważ obiekt został pomyślnie uruchomiony, wszelkie sprawdzanie poprawności, wymuszane przez Konstruktor ma zakończyło się pomyślnie.  
  
### <a name="using-ixmlserializable"></a>Przy użyciu interfejsu IXmlSerializable  
 Zastosuj poniższe najlepsze rozwiązania dla typów implementujących <xref:System.Xml.Serialization.IXmlSerializable> i są serializowane przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
-   <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> Implementacje metody statycznej musi być `public`.  
  
-   Metody wystąpienia, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs musi być `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Przy użyciu programu WCF z kod platformy w pełni zaufany, który umożliwia wywołania z częściowo zaufane obiekty wywołujące  
 Model zabezpieczeń WCF częściowej relacji zaufania przyjęto założenie, że każdego obiektu wywołującego w publicznej metody WCF lub właściwości działa w kontekście zabezpieczeń (CAS) dostępu do kodu aplikacji hostingu. Usługi WCF założono również, istnieje tej aplikacji tylko jeden kontekst zabezpieczeń dla każdego <xref:System.AppDomain>, i ustanowionej w tym kontekście <xref:System.AppDomain> czas utworzenia przez zaufanego hosta (na przykład przez wywołanie do <xref:System.AppDomain.CreateDomain%2A> lub przez Menedżera aplikacji ASP.NET).  
  
 Ten model zabezpieczeń ma zastosowanie do aplikacji zapisane przez użytkownika, które nie assert dodatkowe uprawnienia urzędów certyfikacji, na przykład kod użytkownika uruchomiony w aplikacji ASP.NET zaufania średnia liczba godzin. Jednak kod platformy w pełni zaufane (na przykład innych firm zestawu, który jest zainstalowany w globalnej pamięci podręcznej zestawów i akceptuje połączenia z częściowo zaufanego kodu) musi Zwróć uwagę na jawne wywoływanie WCF imieniu częściowo zaufanych aplikacji Unikaj wprowadzenie luk w zabezpieczeniach na poziomie aplikacji.  
  
 Kod pełnego zaufania, należy unikać Zmienianie zestaw uprawnień urzędów certyfikacji bieżącego wątku (przez wywołanie metody <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, lub <xref:System.Security.PermissionSet.Deny%2A>) przed wywołaniem interfejsów API usługi WCF w imieniu częściowo zaufany kod. Potwierdzające, odmawianie lub w przeciwnym razie tworzenie kontekstu uprawnienia właściwe dla wątków, która jest niezależna od kontekstu zabezpieczeń na poziomie aplikacji może spowodować nieoczekiwane zachowanie. W zależności od aplikacji to zachowanie może spowodować luk w zabezpieczeniach na poziomie aplikacji.  
  
 Kod, który wywołuje WCF za pomocą kontekstu właściwe dla wątków uprawnienia muszą być przygotowane do obsługi następujących sytuacji, które mogą wystąpić podczas:  
  
-   Kontekst zabezpieczeń właściwe dla wątków może się nie powieść w czasie trwania operacji, która powoduje potencjalnych wyjątki zabezpieczeń.  
  
-   Wewnętrzny kod WCF, a także wszystkie wywołania zwrotne dostarczane przez użytkownika może działać w kontekście zabezpieczeń inną niż jeden, pod którym pierwotnie zainicjowano wywołanie. Konteksty te obejmują:  
  
    -   Kontekst uprawnienia aplikacji.  
  
    -   Żadnego kontekstu uprawnienia właściwe dla wątków utworzone wcześniej przez inne wątki użytkownika używane do wywołują WCF przez cały okres istnienia aktualnie uruchomionych <xref:System.AppDomain>.  
  
 WCF gwarantuje, że częściowo zaufany kod nie może uzyskać uprawnienia pełnego zaufania, chyba że takich uprawnień są oceniane pod przez składnik przed wywołaniem w publicznych interfejsach API WCF w pełni zaufanych. Jednak go nie gwarantuje, że skutki potwierdzające pełnego zaufania jest izolowana do określonego wątku, operacji lub akcji użytkownika.  
  
 Najlepszym rozwiązaniem uniknąć tworzenia kontekstu właściwe dla wątków uprawnienia, wywołując <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, lub <xref:System.Security.PermissionSet.Deny%2A>. Zamiast tego należy udzielić lub odmówić uprawnień do aplikacji, dzięki czemu nie <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, lub <xref:System.Security.PermissionSet.PermitOnly%2A> jest wymagana.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>

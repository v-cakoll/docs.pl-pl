---
title: Opracowywanie potoku
ms.date: 03/30/2017
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f981d667f3cbf35ab010ac5bd26a9ecd5c2aae11
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151346"
---
# <a name="pipeline-development"></a>Opracowywanie potoku
Potok dodatku jest ścieżka segmenty potoku, których aplikacja hosta i jego dodatku musi komunikować się ze sobą.  
  
 Na poniższej ilustracji przedstawiono potok komunikacji i jego segmentów.  
  
 ![Dodaj&#45;w modelu potoku. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Potok dodatku  
  
 Aplikacja hosta jest na jednym końcu potoku i dodatek jest na końcu. Począwszy od zakończenia każdego przenoszenie kierunku środka, zarówno aplikacji hosta, jak i dodatku się abstrakcyjna klasa bazowa, definiujący widok modelu obiektów, które współużytkują one zarówno. Te typy (grupy) tworzą segmentów potoku dodatku widoku oraz widoku hosta segmentów potoku dodatku. Segmentów potoku dodatku widoku często zawiera więcej niż jednej klasy abstrakcyjnej, ale klasa, która dodatek dziedziczy jest znany jako podstawowy dodatek.  
  
 Segment potoku karty add w side i Konwertuj segment potoku adaptery po stronie hosta przepływu typów między ich segmenty potoku widoku i segmentów potoku kontraktu. Centralna segmentów potoku jest kontraktu, który jest tworzony na podstawie <xref:System.AddIn.Contract.IContract> interfejsu. Ten kontrakt definiuje metody, które aplikacja hosta i jego dodatek zarówno użyje.  
  
 Jeśli załadujesz hostem a dodatkiem do domen aplikacji w oddzielnych, masz izolującą granicę oddzielający zakresu aplikacji hosta z zakresu od dodatku. Kontrakt jest tylko zestaw, który jest załadowany do hosta i domen aplikacji w dodatku. Hosta i Dodaj do każdego dotyczą tylko swój widok metody kontraktu. W związku z tym są rozdzielone przez warstwę abstrakcji z umowy.  
  
 Aby opracować segmenty potoku, należy utworzyć strukturę katalogów, która będzie zawierać je. Aby uzyskać więcej informacji o wymaganiach dotyczących tworzenia i wytyczne dotyczące zakresu, zobacz [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 Poniższa ilustracja przedstawia typy, które tworzą segmenty potoku. Nazwy typów przedstawiono na rysunku są dowolne, ale wszystkich typów, z wyjątkiem hosta i hosta wyświetlić atrybutów wymagają dodatku, dzięki czemu mogą oni zostać odnalezieni za pomocą metod, które konstruowania Magazyn informacji.  
  
 ![Dodaj&#45;w modelu z wymaganych atrybutów dla typów. ](../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Potok dodatku z typami  
  
 W poniższej tabeli opisano segmenty potoku do aktywacji dodatku. Aby uzyskać więcej informacji na temat tych segmentach zobacz [kontrakty, widoki i adaptery](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Segment potoku|Opis|  
|----------------------|-----------------|  
|Host|Zestaw aplikacji, który tworzy wystąpienie klasy dodatku.|  
|Widok hosta dodatków|Reprezentuje widok aplikacji hosta typy obiektów i metod używanych do komunikowania się z dodatku. Widok hosta jest abstrakcyjna klasa bazowa lub interfejs.|  
|Adaptery po stronie hosta|Zestaw z co najmniej jedną klasę, która dostosowuje się metody do i z umowy.<br /><br /> Ten segment potoku jest identyfikowany przy użyciu <xref:System.AddIn.Pipeline.HostAdapterAttribute> atrybutu.<br /><br /> Zestawy wielu modułów są nieobsługiwane.|  
|Kontrakt|Interfejs, który jest tworzony na podstawie <xref:System.AddIn.Contract.IContract> interfejsu i który definiuje protokół komunikacji typów między hostem a jego dodatku.<br /><br /> Ten segment potoku jest identyfikowany przez ustawienie <xref:System.AddIn.Pipeline.AddInContractAttribute> atrybutu.|  
|Dodawanie strony karty|Zestaw z co najmniej jedną klasę, która dostosowuje się metody do i z umowy.<br /><br /> Ten segment potoku jest identyfikowany przy użyciu <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu.<br /><br /> Każdego zestawu w katalogu karty Dodaj strony, który zawiera typ, który ma <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu jest ładowany do dodatku w domenie aplikacji.<br /><br /> Każdego zestawu w katalogu add w side jest ładowany w domenie aplikacji.<br /><br /> Zestawy wielu modułu nie są obsługiwane.|  
|Widok dodatku|Zestaw, który reprezentuje Widok dodatku typy obiektów i metod, które są używane do komunikacji z hostem. Widok dodatku jest abstrakcyjna klasa bazowa lub interfejs.<br /><br /> Ten segment potoku jest identyfikowany przy użyciu <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu.<br /><br /> Każdego zestawu w katalogu AddInViews, który zawiera typ, który ma <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu jest ładowany do dodatku w domenie aplikacji.|  
|Dodatek|Skonkretyzowany typ, który wykonuje usług dla hosta.|  
  
## <a name="pipeline-activation-path"></a>Ścieżka aktywacji potoku  
 Poniższa ilustracja przedstawia aktywacji typów, gdy dodatek jest aktywny. Zawiera również przekazywanie obiektów do hosta, takie jak wyniki obliczeń lub kolekcji obiektów. Jest to najbardziej typowym scenariuszem.  
  
 ![Dodaj&#45;w modelu przy użyciu ścieżki aktywacji. ](../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Ścieżka aktywacji w dodatku do hosta  
  
 Ścieżka aktywacji potoku odbywa się w następujący sposób:  
  
1.  Aplikacja hosta aktywuje dodatek za pomocą <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metody.  
  
2.  Widok dodatku, dodatek, karta add w side i zestawy umowy są ładowane do dodatku w domenie aplikacji.  
  
3.  Przy użyciu widoku dodatku, tworzone jest wystąpienie karty add w side (przy użyciu klasy identyfikowane przez <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu) jako jego konstruktora. Karta Dodaj w side dziedziczy z umowy.  
  
4.  Karty Dodaj strony, która jest jako wpisana nazwa kontraktu, jest przekazywany przez granicę izolacji (opcjonalnie) do konstruktora adapter po stronie hosta.  
  
5.  Widok hosta karty dodatku, po stronie hosta i zestawy umowy są ładowane do domeny aplikacji hosta.  
  
6.  Tworzone jest wystąpienie adapter po stronie hosta, za pomocą umowy jako jej konstruktora. Adaptery po stronie hosta dziedziczy widok hosta dodatków.  
  
7.  Host ma dodatku, którego typem hosta Widok dodatku i można kontynuować wywoływania jego metody.  
  
## <a name="walkthroughs"></a>Wskazówki  
 Istnieją trzy instruktaże, które zawierają opis sposobu tworzenia potoków przy użyciu programu Visual Studio:  
  
-   [Wskazówki: Tworzenie aplikacji rozszerzalnej](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     W tym artykule opisano dodatek Kalkulator, który wykonuje Dodawanie, odejmowanie, mnożenie i dzielenie obliczeń dla hosta.  
  
-   [Wskazówki: Włączanie zgodności z poprzednimi wersjami w miarę zmieniania hosta](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     W tym artykule opisano Kalkulator dodatek za pomocą obliczeń rozszerzone możliwości oraz sposobu utrzymania zgodności z pierwszą Kalkulator dodatku programu.  
  
-   [Wskazówki: Przekazywanie kolekcji między hostami i dodatkami](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     W tym artykule opisano sposób przekazywania zbierania danych przez potok przy użyciu scenariusza magazynu książki.  
  
## <a name="see-also"></a>Zobacz też  
- [Scenariusze potoku dodatku](https://msdn.microsoft.com/library/feb70e0b-8734-494c-aeaf-b567f014043e)  
- [Dodatki i rozszerzalność](../../../docs/framework/add-ins/index.md)

---
title: Obsługa wielu wiązań witryny usług IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 5a8b06d86b505452f9ded808f727343b1453e592
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696109"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Obsługa wielu wiązań witryny usług IIS
W przypadku hostowania usługi Windows Communication Foundation (WCF) w obszarze Internetowe usługi informacji (IIS) 7.0, można podać wiele podstawowych adresów, które używają tego samego protokołu w tej samej lokacji. Dzięki temu tę samą usługę odpowiedzieć na szereg różnych identyfikatorów URI. Jest to przydatne, gdy chcesz umieścić to usługa, która nasłuchuje na `http://www.contoso.com` i `http://contoso.com`. Jest to również przydatne utworzyć usługę, która ma adres podstawowy dla użytkowników wewnętrznych i oddzielnych adres podstawowy dla użytkowników zewnętrznych. Na przykład: `http://internal.contoso.com` i `http://www.contoso.com`.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko przy użyciu protokołu HTTP.  
  
## <a name="multiple-base-addresses"></a>Wiele adresów podstawowy  
 Ta funkcja jest dostępna tylko do usług WCF, które są hostowane w usługach IIS. Ta funkcja nie jest włączona domyślnie. Aby ją włączyć, należy dodać `multipleSiteBindingsEnabled` atrybutu <`serviceHostingEnvironment`> elementu w z pliku Web.config plik i ustaw ją na `true`, jak pokazano w poniższym przykładzie.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 W przypadku hostowania usługi WCF w środowisku usług IIS, usługi IIS tworzą jeden adres bazowy na podstawie identyfikatora URI do katalogu wirtualnego, który zawiera aplikację. Możesz dodać dodatkowe adresy podstawowy, które używają tego samego protokołu za pomocą Menedżera internetowych usług informacyjnych, aby dodać co najmniej jedno powiązanie do witryny sieci Web. Dla każdego powiązania określić protokół (HTTP lub HTTPS), adres IP, portu i nazwy hosta. Aby uzyskać więcej informacji na temat używania Menedżera internetowych usług informacyjnych, zobacz [Menedżera internetowych usług informacyjnych (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164057). Aby uzyskać więcej informacji na temat dodawania powiązania witryny zobacz [Utwórz witrynę sieci Web (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Określanie wielu adresami podstawowymi dla tej samej lokacji ma wpływ na zawartość strony pomocy usługi WCF, importowanie schematu i informacje o WSDL/MEX, generowane przez usługę. Stronę pomocy WCF wyświetla wiersz poleceń do generowania klienta WCF, który może komunikować się z usługą. Ten wiersz polecenia zawiera tylko pierwszy adres określonej w powiązaniu usługi IIS dla witryny sieci Web. Podobnie podczas importowania schematu, tylko adres podstawowy pierwszego określonej w powiązaniu usług IIS jest używana. Dane WSDL oraz MEX zawierać wszystkie adresy podstawowy określony w powiązań usług IIS.  
  
> [!WARNING]
>  Oznacza to, że jeśli usługa ma dwa adresy podstawowy, jeden dla użytkowników wewnętrznych i jeden dla użytkowników zewnętrznych, są określone oba w informacjach o WSDL/MEX wygenerowanej przez usługę.

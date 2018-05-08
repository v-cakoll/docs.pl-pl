---
title: Obsługa wielu powiązań witryny usług IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 9b92243bb7aaea5c8ecf708ce863e6979bc9f17c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="supporting-multiple-iis-site-bindings"></a>Obsługa wielu powiązań witryny usług IIS
Hosting usługi Windows Communication Foundation (WCF) w obszarze Internet informacji Services (IIS) 7.0, możesz podać wiele adres podstawowy, które używają tego samego protokołu na tej samej lokacji. Dzięki tej samej usługi odpowiedzieć na szereg różnych identyfikatorów URI. Jest to przydatne, jeśli chcesz obsługiwać usługę, która nasłuchuje na http://www.contoso.com i http://contoso.com. Warto również utworzyć usługę, która ma adres podstawowy dla użytkowników wewnętrznych i oddzielne adres podstawowy dla użytkowników zewnętrznych. Na przykład: http://internal.contoso.com i http://www.contoso.com.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko przy użyciu protokołu HTTP.  
  
## <a name="multiple-base-addresses"></a>Wiele adresów bazowych  
 Ta funkcja jest dostępna tylko do usług WCF, które są obsługiwane w środowisku usług IIS. Ta funkcja nie jest włączona domyślnie. Aby ją włączyć, należy dodać `multipleSiteBindingsEnabled` atrybutu <`serviceHostingEnvironment`> elementu w pliku Web.config pliku i ustaw ją na `true`, jak pokazano w poniższym przykładzie.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Odnośnie do hostowania usługi WCF w środowisku usług IIS, usługi IIS tworzą jeden adres podstawowy, na podstawie identyfikatora URI do katalogu wirtualnego, który zawiera aplikację. Możesz dodać dodatkowe adresy podstawowy, które używają tego samego protokołu za pomocą Menedżera internetowych usług informacyjnych dodać co najmniej jednego powiązania do witryny sieci Web. Dla każdego powiązania określić protokół (HTTP lub HTTPS), adres IP, portu i nazwy hosta. Aby uzyskać więcej informacji na temat korzystania z Menedżera internetowych usług informacyjnych, zobacz [Menedżera internetowych usług informacyjnych (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). Aby uzyskać więcej informacji na temat dodania powiązań do witryny, zobacz [utworzyć witrynę sieci Web (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Określanie wielu adresu podstawowego dla tej samej lokacji dotyczy zawartości strony pomocy WCF Importowanie schematu i informacji WSDL/MEX wygenerowanej przez usługę. Strona pomocy WCF wyświetla wiersz polecenia używany do generowania klienta WCF, który może komunikować się z usługą. Ten wiersz polecenia zawiera tylko pierwszy adres określony w powiązaniu usługi IIS dla witryny sieci Web. Podobnie podczas importowania schematu, tylko adres podstawowy pierwszego określony w powiązaniu usług IIS jest używana. Dane WSDL oraz MEX zawierać adres podstawowy określony w powiązania usługi IIS.  
  
> [!WARNING]
>  Oznacza to, że jeśli usługa ma dwa adresy podstawowy, jeden dla użytkowników wewnętrznych i jeden dla użytkowników zewnętrznych, są określone w informacji WSDL/MEX wygenerowanej przez usługę.

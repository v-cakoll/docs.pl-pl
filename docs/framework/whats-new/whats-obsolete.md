---
title: Co&#39;s przestarzałe w bibliotece klas programu .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01969eff86e5b1e8e4e2bdc4950df9fb5291f5b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514453"
---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a>Co&#39;s przestarzałe w bibliotece klas programu .NET Framework
.NET Framework zmienia się wraz z upływem czasu. Każda nowa wersja dodaje nowe typy i elementy członkowskie typu, które zapewniają nowe funkcje. Istniejących typów i ich elementy członkowskie także ulec zmianie. Na przykład niektóre typy stają się mniej ważne technologii, które obsługują zastępuje to nowa technologia, a niektóre metody są zastępowane przez nowszą metod, które są bardziej wygodne lub zaawansowanych funkcji.  
  
 .NET Framework i środowisko uruchomieniowe języka wspólnego dążyć do obsługi zgodności z poprzednimi wersjami (dzięki czemu aplikacje, które zostały opracowane z jednej wersji programu .NET Framework do uruchamiania na następną wersję programu .NET Framework). Utrudnia to po prostu usuń typu lub elementu członkowskiego typu. Zamiast tego programu .NET Framework wskazuje, czy typ lub element członkowski typu powinna już być używana przez oznaczenie jej jako przestarzałe lub przestarzałe. Wycofano typ lub element członkowski obejmuje oznaczenie go tak, aby deweloperzy wiedzą zostanie zniknie i czas odpowiedzieć na jego usunięcia. Jednak istniejący kod, który używa typu lub elementu członkowskiego jest nadal uruchomione w nowej wersji programu .NET Framework.  
  
> [!NOTE]
>  Warunki *przestarzałe* i *przestarzałe* ma takie samo znaczenie, gdy jest stosowany do typy i elementy członkowskie programu .NET Framework.  
  
## <a name="the-obsoleteattribute-attribute"></a>Atrybut ObsoleteAttribute  
 .NET Framework wskazuje, że typ lub element członkowski typu jest przestarzały przez oznaczenie go atrybutem <xref:System.ObsoleteAttribute> atrybutu. Stosowanie atrybut do typu lub elementu członkowskiego wskazuje, czy czy typ lub element członkowski zostanie usunięta w niektórych przyszłej wersji programu .NET Framework bez podziału skompilowany kod, który używa tego elementu członkowskiego.  
  
 Oprócz wskazująca, że typ lub element członkowski typu jest przestarzały, <xref:System.ObsoleteAttribute> definiuje sposób obsługi przez kompilator kodu źródłowego, który zawiera tego typu lub elementu członkowskiego. Kompilator można skompilować kod, ale Emituj komunikat ostrzegawczy lub go traktować użycie typu lub elementu członkowskiego jako błąd. W pierwszym przypadku pomyślnie można skompilować kodu, ale komunikat ostrzegawczy wskazuje, że typ lub element członkowski jest przestarzały. W drugim przypadku kompilacja kończy się niepowodzeniem.  
  
 Nawet jeśli kompilacja generuje błąd zamiast komunikat ostrzegawczy <xref:System.ObsoleteAttribute> nie ma wpływu na zachowanie czasu wykonania. Oznacza to, że aplikacje, które używają typu lub elementu członkowskiego i która została wykonana pomyślnie zawsze będą uruchomione pomyślnie. Tylko próba ponownie skompilować aplikację, która używa typu lub elementu członkowskiego nie powiedzie się.  
  
## <a name="how-to-handle-obsolete-types-and-members"></a>Sposób obsługi przestarzałe typy i elementy członkowskie  
 Podczas uaktualniania i skompiluj ponownie istniejący kod, za pomocą przestarzałego typu lub elementu członkowskiego, który generuje ostrzeżenie kompilatora w aplikacji jest dopuszczalne idealnie. Należy jednak przejrzeć komunikat ostrzegawczy kompilatora, aby określić, czy należy zmienić kod aplikacji. Jeśli wiadomość nie wskazuje odpowiedniego alternatywnego rozwiązania, należy wykonać następujące czynności:  
  
-   Zmienić swój kod zrezygnowanie z użycia typu lub elementu członkowskiego, jeśli to możliwe.  
  
     —lub—  
  
-   Zapoznaj się z dokumentacją dla tego obszaru technologii ustalenie sposobu reagowania na wycofywanie.  
  
 Można pominąć ponowne skompilowanie istniejącego kodu przy użyciu nowszej wersji programu .NET Framework. Zamiast tego można określić wersji programu .NET Framework, względem którego istniejącą skompilowany kod działa. Na przykład, załóżmy, że masz aplikację o nazwie app1.exe, który został skompilowany [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ale chcesz aplikacji w celu uruchomienia [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. To wymaga wykonania następujących czynności:  
  
1.  Utwórz plik konfiguracji do głównego pliku wykonywalnego i nadaj mu nazwę *appName*. exe.config, gdzie *appName* jest nazwą pliku wykonywalnego aplikacji. Dla aplikacji o nazwie app1.exe w naszym przykładzie należy utworzyć plik konfiguracji o nazwie app1.exe.config.  
  
2.  Dodaj następujący element do pliku konfiguracji.  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 W poniższej tabeli wymieniono wartości ciągów, które można przypisać do `version` atrybutu pod kątem określonej wersji programu .NET Framework.  
  
|Wersja programu .NET Framework|`version` Ciąg|
|-|-|  
|4.7 (w tym 4.7.1 i 4.7.2)|wersja 4.0|  
|4.6 (w tym 4.6.1 i 4.6.2)|wersja 4.0|  
|4.5 (w tym 4.5.1 i 4.5.2)|wersja 4.0|  
|4|wersja 4.0|  
|3.5|v2.0.50727|  
|2.0|v2.0.50727|  
|1.1|V1.1.4322|  
|1.0|V1.0.3705|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a>Przestarzałe list dla platformy .NET Framework 4.5 lub nowszy  
 [Przestarzałe typy](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [Przestarzałe elementy członkowskie](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a>Przestarzałe list w poprzednich wersjach  
 [Przestarzałe typy w programie .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [Przestarzali członkowie w programie .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [.NET framework 3.5 przestarzałe listy](http://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [.NET framework 2.0 przestarzałe listy](http://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a>Zobacz też  
 [\<supportedRuntime > — Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)

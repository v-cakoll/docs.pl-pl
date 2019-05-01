---
title: 'Instrukcje: Tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c26c84ece1231a4e118144c163fa3e9c7619301
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875748"
---
# <a name="how-to-create-com-wrappers"></a>Instrukcje: Tworzenie otok COM

Otoki Component Object Model (COM) można utworzyć za pomocą funkcji Visual Studio 2005 lub narzędzi programu .NET Framework, Tlbimp.exe i Regasm.exe. Obie metody wygenerować dwa typy otok COM:

- A [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) z biblioteki typów, aby uruchomić obiektów COM w kodzie zarządzanym.

- A [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md) za pomocą ustawień rejestru wymagane do uruchamiania zarządzanego obiektu w aplikacji natywnej.

W programie Visual Studio 2005 można dodać otoki COM jako odwołanie do projektu.

## <a name="wrap-com-objects-in-a-managed-application"></a>Zawiń obiektów COM w aplikacji zarządzanej

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Aby utworzyć wywoływana otoka środowiska uruchomieniowego przy użyciu programu Visual Studio

1. Otwórz projekt dla aplikacji zarządzanej.

2. Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.

3. Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.

4. W oknie dialogowym Dodaj odwołanie, kliknij przycisk **COM** , a następnie wybierz składnik, należy użyć, a następnie kliknij przycisk **OK**.

     W **Eksploratora rozwiązań**, należy pamiętać, że składnik COM został dodany do folderu odwołań w projekcie.

Teraz można napisać kod, aby uzyskać dostęp do obiektu COM. Możesz rozpocząć od zadeklarowania obiektu, takie jak za pomocą `Imports` poufności informacji dotyczące [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] lub `Using` poufności informacji dotyczące [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].

> [!NOTE]
> Jeśli chcesz program Microsoft Office składniki, najpierw zainstaluj [podstawowe zestawy międzyoperacyjne pakietu Office Microsoft](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z Microsoft Download Center. W kroku 4, wybierz najnowszą dostępną dla produktu Office ma, takich jak biblioteki obiektów **Biblioteka obiektów programu Microsoft Word 11.0**.  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Aby utworzyć wywoływana otoka środowiska uruchomieniowego przy użyciu narzędzi programu .NET Framework  
  
- Uruchom [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) narzędzia.  
  
 To narzędzie tworzy zestaw, który zawiera metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnej biblioteki typów.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>OPAKOWYWANIE zarządzanych obiektów w aplikacji macierzystej  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Aby utworzyć wywołalne opakowanie COM za pomocą programu Visual Studio  
  
1. Utwórz projekt biblioteki klas dla zarządzanej klasy, która ma zostać uruchomiony w kodzie natywnym. Klasa musi mieć domyślnego konstruktora.  
  
     Sprawdź, czy masz pełną Czteroczęściowy numer wersji zestawu w pliku AssemblyInfo. Ta liczba jest wymagany do obsługi przechowywania wersji w rejestrze systemu Windows. Aby uzyskać więcej informacji na temat numerów wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
3. Kliknij przycisk **skompilować** kartę.  
  
4. Wybierz **Zarejestruj dla współdziałania COM** pole wyboru.  
  
 Podczas kompilowania projektu zestawu jest automatycznie rejestrowane dla współdziałania z modelem COM. Jeśli tworzysz natywnych aplikacji w programie Visual Studio 2005, można użyć zestawu, klikając **Dodaj odwołanie** na **projektu** menu.  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Aby utworzyć wywołalne opakowanie COM za pomocą narzędzi programu .NET Framework  
  
Uruchom [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) narzędzia.  
  
To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru. W rezultacie klientów modelu COM może przezroczyste Tworzenie klas .NET Framework. Można użyć zestawu, tak jakby natywnych klasa COM.  
  
Uruchamianie Regasm.exe na zestawu znajdującego się w dowolnym katalogu, a następnie uruchom [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) przenieść je do globalnej pamięci podręcznej. Przenoszenie zestawu nie unieważnia wpisy rejestru lokalizacji, ponieważ w globalnej pamięci podręcznej jest badany zawsze, jeśli zestaw nie zostanie znaleziony gdzie indziej.  
  
## <a name="see-also"></a>Zobacz także

- [Wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md)
- [Wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md)

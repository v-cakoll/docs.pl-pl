---
title: Walidacja złożoności haseł
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 7b2d6a81f5dc88688a469b96d56a098a2b45c59f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363689"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Wskazówki: sprawdzanie poprawności złożoności haseł (Visual Basic)
Ta metoda sprawdza pewne cechy silnego hasła i aktualizuje parametr ciągu z informacjami o tym, które sprawdzenia nie powiodło się.  
  
 Hasła mogą być używane w zabezpieczonym systemie w celu autoryzowania użytkownika. Jednak hasła muszą być trudne dla nieautoryzowanych użytkowników. Osoby atakujące mogą korzystać z programu *ataku słownikowego* , który wykonuje iterację we wszystkich słowach w słowniku (lub wielu słownikach w różnych językach) i sprawdza, czy którykolwiek z tych słów działa jako hasło użytkownika. Słabe hasła, takie jak "Yankees" lub "Mustang", można szybko wypróbować. Silniejsze hasła, na przykład "? " L1N3vaFiNdMeyeP@sSWerd !", Są znacznie mniej podobne do odgadnięcia. System chroniony hasłem powinien mieć pewność, że użytkownicy wybierają silne hasła.  
  
 Silne hasło jest złożone (zawierające kombinację wielkich, małych liter, cyfr i znaków specjalnych) i nie jest słowem. W tym przykładzie pokazano, jak sprawdzić złożoność.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Wywołaj tę metodę, przekazując ciąg, który zawiera to hasło.  
  
 Ten przykład wymaga:  
  
- Dostęp do elementów członkowskich <xref:System.Text.RegularExpressions> przestrzeni nazw. Dodaj `Imports` instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Zabezpieczenia  
 Jeśli przenosisz hasło za pośrednictwem sieci, musisz użyć bezpiecznej metody przesyłania danych. Aby uzyskać więcej informacji, zobacz [ASP.NET zabezpieczenia aplikacji sieci Web](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 Dokładność funkcji można poprawić `ValidatePassword` , dodając dodatkowe sprawdzenia złożoności:  
  
- Porównaj hasło i jego podciągi w odniesieniu do nazwy użytkownika, identyfikatora użytkownika i słownika zdefiniowanego przez aplikację. Ponadto Traktuj podobne wizualnie znaki jako równoważne podczas przeprowadzania porównania. Na przykład Traktuj litery "l" i "e" jako równoważne cyfrom "1" i "3".  
  
- Jeśli istnieje tylko jeden znak pisany wielkimi literami, upewnij się, że nie jest on pierwszym znakiem hasła.  
  
- Upewnij się, że ostatnie dwa znaki hasła są literami znaków.  
  
- Nie Zezwalaj na hasła, w których wszystkie symbole są wprowadzane z górnego wiersza klawiatury.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Text.RegularExpressions.Regex>
- [Zabezpieczenia aplikacji sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))

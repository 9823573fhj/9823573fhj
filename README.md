using System;
using System.Collections.Generic;

class Program
{
    static int vidaCedric = 100;
    static bool armadilhaAtivada = false;
    static bool batalhaAtiva = false;
    static Inimigo inimigoAtual;
    static List<Item> inventario = new List<Item>();
    private static string nome;
    static List<Inimigo> inimigosDerrotados = new List<Inimigo>();

    static void Main()
    {
       Console.WriteLine("Bem-vindo ao Jogo de Fantasia Medieval!");
        Console.WriteLine("Neste jogo, você assumirá o papel de Cédric, um príncipe exilado em busca de vingança contra seu tio Moros, que usurpou o trono após matar seu pai Magnus.");
Console.WriteLine("Bem-vindo ao Jogo de Fantasia Medieval!");
        Console.WriteLine("Neste jogo, você vai assumir o papel de Cédric, um príncipe exilado que busca vingança contra seu tio Moros, que matou seu pai Magnus e usurpou o trono.");

        Console.WriteLine("Você vai enfrentar vários desafios e perigos em sua jornada, e suas escolhas vão determinar o seu destino.");
        Console.WriteLine("Digite o seu nome e pressione ENTER para começar:");

        nome = Console.ReadLine();

        Console.Clear();

        Console.WriteLine(" Você é Cédric, o filho mais novo do rei Magnus, que governava o reino de Elingard com sabedoria e justiça.");
        Console.WriteLine("Você é uma criança que após perder sua mãe no parto, é criado por seu pai Magnus, filho do imperador Zoa, quem criou o Reino de Elingard.");
        Console.WriteLine("Magnus foi criado com seu irmão Moros que sempre tiveram uma relação conturbada, e logo após a morte do seu pai, onde Zoa antes de morrer escolheu Magnus como herdeiro do trono só piorou.");
        Console.WriteLine("Moros era o governante de uma província vizinha e sempre invejou o poder e a riqueza de seu irmão.");
        Console.WriteLine("Ele planejou secretamente um golpe de estado e aproveitou uma noite em que estava hospedado no castelo real para executar seu plano.");
        Console.WriteLine("Cinco anos após o nascimento de Cédric, seu tio Moros faz o golpe e toma o trono de Magnus, além disso, o mata na frente de seu filho. Logo após, ele tenta fazer o mesmo com o primogênito.");
        Console.WriteLine("Você conseguiu escapar com a ajuda de Lewis, o braço direito de seu pai.");
        Console.WriteLine("Na fuga, devido à perseguição de Moros e seus soldados, Cédric acaba se machucando e desmaia. Quando acorda, Cédric não se lembra de nada, só percebe que foi resgatado por um casal de camponeses que o cuidam como filho.");
        Console.WriteLine("Pressione qualquer tecla para continuar...");

        Console.ReadKey();

        Console.Clear();

        Console.WriteLine("O tempo se passa e Cédric acaba de se tornar um adulto, onde ele se tornou um herói amado pelos camponeses, pois ele protege o campo contra saqueadores e guardas que tentam se aproveitar dos moradores.");
        Console.WriteLine("Sua força e determinação ficaram conhecidas em todos os cantos do reino, e rapidamente chamaram atenção.");
        Console.WriteLine("Em aparentemente mais um dia comum, Cédric acorda assustado com várias batidas na porta de sua casa. Seus pais tinham acabado de sair para ir fazer a colheita, o que o obrigava a ir atender. Quando Cédric abre, se depara com um homem estranho que o cumprimenta com euforia. Sem entender nada, pergunta o que está acontecendo. O sujeito estranho o entrega um amuleto e logo após ele o pegar na mão, todas as lembranças do seu passado voltam de uma vez, que ao recordar resolve iniciar uma vingança contra o seu tio que tomou o trono de seu pai.");
        Console.WriteLine("Logo após, Lewis revela outro fato. Magnus era muito forte, sendo fisicamente o mais forte do reino quando estava vivo. Sua mãe era uma das melhores magas de Elingard. Quando Cédric nasceu, antes de sua mãe morrer, ela colocou seus poderes mágicos juntamente com a força de Magnus, no seu filho, mas só o Cédric consegue descobrir como libertá-los.");
        Console.WriteLine("Lewis continua e lembra Cédric do torneio Wingard que ocorre a cada década, onde os cidadãos têm a chance de conquistar o trono se passarem de todas as fases da competição, e tendo como objetivo final derrotar o atual rei. O grande problema é que Cédric teria só uma semana para treinar.");
        Console.WriteLine("Pressione qualquer tecla para continuar...");

        Console.ReadKey();

        Console.Clear();

        Console.WriteLine("Cédric se despede de seus pais e parte para treinar junto com Lewis em apenas 5 dias que ainda restam para eles.");
        Console.WriteLine("Dois dias eram viajando para Elingard. Lewis leva seu aprendiz para uma caverna, Cédric inicialmente reluta e questiona Lewis. Lewis apenas fica em silêncio e aponta para a caverna. Mesmo sem entender, o jovem entra.");
        Console.WriteLine("Lá Lewis quebra o silêncio e explica que nesses 5 dias Cédric iria meditar, pois por ser um guerreiro, o poder bruto ele já tinha, mas as técnicas e as magias do seu pai ainda estavam dentro dele, e só quem poderia desbloquear elas era ele.");
        Console.WriteLine("Ele concorda e se despedindo de Lewis, ele promete dar o seu melhor.");
        Console.WriteLine("Nesses dias, Cédric treinou não só o físico, mas por ter se isolado de tudo, ele se encontrou e despertou os seus poderes. Quando Lewis vem buscá-lo, fica impressionado com o desenvolvimento de seu aluno, e juntos partem para Elingard.");
        Console.WriteLine("Pressione qualquer tecla para continuar...");
        Console.WriteLine("Digite o seu nome e pressione ENTER para começar:");
        nome = Console.ReadLine();
        Console.Clear();

        

        AdicionarInimigos(); 

        while (true)
        {
            Console.WriteLine("\nEscolha uma ação:");
            Console.WriteLine("1. Avançar para a próxima sala");
            Console.WriteLine("2. Olhar ao redor");
            Console.WriteLine("3. Pegar item");
            Console.WriteLine("4. Ver inventário");
            Console.WriteLine("5. Sair do jogo");

            string escolha = Console.ReadLine();

            switch (escolha)
            {
                case "1":
                    AndarParaFrente();
                    break;
                case "2":
                    OlharAoRedor();
                    break;
                case "3":
                    PegarItem();
                    break;
                case "4":
                    MostrarInventario();
                    break;
                case "5":
                    Console.WriteLine("Até logo!");
                    Environment.Exit(0);
                    break;
                default:
                    Console.WriteLine("Escolha inválida. Tente novamente.");
                    break;
            }

            if (batalhaAtiva)
            {
                RealizarBatalha();

               
                if (TodosInimigosDerrotados())
                {
                    Console.WriteLine("Parabéns, " + nome + "! Você derrotou todos os inimigos. Você venceu o jogo!");
                    Environment.Exit(0);
                }
            }

            if (vidaCedric <= 0)
            {
                Console.WriteLine("Você foi derrotado. Fim de jogo!");
                Environment.Exit(0);
            }
        }
    }

    private static void AdicionarInimigos()
    {
        throw new NotImplementedException();
    }

    static void AndarParaFrente()
    {
        Console.WriteLine("Você avançou para a próxima sala.");

       
        if (!armadilhaAtivada)
        {
            Console.WriteLine("Você caiu em uma armadilha! Perdeu 20 de vida.");
            vidaCedric -= 20;
            armadilhaAtivada = true;
            batalhaAtiva = true;

           
            EscolherInimigoAleatorio();
            Console.WriteLine("Um " + inimigoAtual.Nome + " apareceu!");
        }
        else
        {
            Console.WriteLine("Nenhuma armadilha encontrada.");
            batalhaAtiva = false;
        }
    }

    static void OlharAoRedor()
    {
        Console.WriteLine("Você olha ao redor e vê uma criatura inimiga!");

        // Inicia uma batalha
        batalhaAtiva = true;
        EscolherInimigoAleatorio();
        Console.WriteLine("Um " + inimigoAtual.Nome + " apareceu!");
    }

    static void PegarItem()
    {
        Console.WriteLine("Você encontrou um item! Ganhou 10 de vida.");
        vidaCedric += 10;
        Console.WriteLine("Vida atual: " + vidaCedric);
    }

    static void MostrarInventario()
    {
        Console.WriteLine("Inventário:");

        if (inventario.Count == 0)
        {
            Console.WriteLine("O inventário está vazio.");
        }
        else
        {
            foreach (Item item in inventario)
            {
                Console.WriteLine("- " + item.Nome);
            }
        }
    }

    static void RealizarBatalha()
    {
        Console.WriteLine("\nBATALHA!");
        Console.WriteLine("Sua vida: " + vidaCedric);
        Console.WriteLine(inimigoAtual.Nome + "'s vida: " + inimigoAtual.Vida);
        Console.WriteLine("Escolha uma ação:");
        Console.WriteLine("1. Atacar");
        Console.WriteLine("2. Defender");
        Console.WriteLine("3. Usar item");

        string escolhaBatalha = Console.ReadLine();

        switch (escolhaBatalha)
        {
            case "1":
                Atacar();
                break;
            case "2":
                Defender();
                break;
            case "3":
                UsarItem();
                break;
            default:
                Console.WriteLine("Escolha inválida. Tente novamente.");
                break;
        }

        Console.WriteLine(inimigoAtual.Nome + " atacou você!");
        vidaCedric -= 10;

       
        if (vidaCedric <= 0)
        {
            Console.WriteLine("Você foi derrotado. Fim de jogo!");
            Environment.Exit(0);
        }
        else if (inimigoAtual.Vida <= 0)
        {
            Console.WriteLine("Você derrotou o " + inimigoAtual.Nome + "!");
            inventario.Add(new Item("Poção de Cura"));
            inimigosDerrotados.Add(inimigoAtual);

            
            batalhaAtiva = false;
        }
    }

    static void Atacar()
    {
        Console.WriteLine("Você atacou o inimigo!");
        inimigoAtual.Vida -= 15;
    }

    static void Defender()
    {
        Console.WriteLine("Você se defendeu.");
        vidaCedric += 5;
    }

    static void UsarItem()
    {
        if (inventario.Count > 0)
        {
            Item itemSelecionado = inventario[0];
            Console.WriteLine("Você usou " + itemSelecionado.Nome + "!");
            vidaCedric += 20;
            inventario.Remove(itemSelecionado);
        }
        else
        {
            Console.WriteLine("Seu inventário está vazio. Nenhum item para usar.");
        }
    }

    static void EscolherInimigoAleatorio()
    {
        Random random = new Random();
        int numeroAleatorio = random.Next(1, 4);

        switch (numeroAleatorio)
        {
            case 1:
                inimigoAtual = new Inimigo("Orc", 50);
                break;
            case 2:
                inimigoAtual = new Inimigo("Goblin", 30);
                break;
            case 3:
                inimigoAtual = new Inimigo("Criatura Sombria", 40);
                break;
        }
    }

    static bool TodosInimigosDerrotados()
    {
       
        return inimigosDerrotados.Count == 3; 

    static void AdicionarInimigos()
    {
        Inimigo orc = new Inimigo("Orc", 50);
        Inimigo goblin = new Inimigo("Goblin", 30);
        Inimigo criaturaSombria = new Inimigo("Criatura Sombria", 40);

        inimigosDerrotados.Add(orc);
        inimigosDerrotados.Add(goblin);
        inimigosDerrotados.Add(criaturaSombria);
    }
}

class Inimigo
{
    public string Nome { get; set; }
    public int Vida { get; set; }

    public Inimigo(string nome, int vida)
    {
        Nome = nome;
        Vida = vida;
    }
}

class Item
{
    public string Nome { get; set; }

    public Item(string nome)
    {
        Nome = nome;
    }
}
}

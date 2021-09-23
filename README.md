# pvp comand minecraft

command /pvp:
    trigger:
        if {pvp.%player%} is not set:
            set {pvp.%player%} to true
            send "&7[&cvoor&fbeeld&9server&7] &aPvP staat nu aan."
        else:
            delete {pvp.%player%}
            send "&7[&cvoor&fbeeld&9server&7] &cPvP staat nu uit."
 
on damage:
    attacker is set
    victim is set
    attacker is a player
    victim is a player
    {pvp.%attacker%} is set:
        {pvp.%victim%} is not set:
            send "&7[&cvoor&fbeeld&9server&7] &c%victim% &cZijn/Haar PvP staat uit" to attacker
            cancel event
    else:
        send "&7[&cvoor&fbeeld&9server&7] &cJouw PvP staat uit gebruik /pvp om dit aan te zetten" to attacker
        cancel event

<script setup>
import Poet from './Poet.vue'
import RimbaudIcon from './icons/IconRimbaud.vue'
import HugoIcon from './icons/IconHugo.vue'
import AntarIcon from './icons/IconAntar.vue'
import HikmetIcon from './icons/IconHikmet.vue'
import NerudaIcon from './icons/IconNeruda.vue'
</script>

<template>
  <Poet>
    <template #icon>
      <NerudaIcon />
    </template>
    <template #heading>Pablo Neruda</template>

    He is considered as one of the for greatest Chilian poets. He obtained the Littereture Nobel price in 1971. <br />
    "<i>And they tell me: "Your people,
your unfortunate people,
between the mountain and the river,

hungry and in pain,
he doesn't want to fight alone, 
and he is waiting for you, friend."

Oh you, the one I love,
small, red pimple
wheat,
the fight will be hard,
life will be hard,
but you will be with me </i>"
  </Poet>

  <Poet>
    <template #icon>
      <HugoIcon />
    </template>
    <template #heading>Victor Hugo</template>
    French romantic poet, writer and novelist, born in 1802 and died in 1885. He is considered one of 
    the most important writers of the French language. 
    He is also a political personality and a committed intellectual who played a major ideological role 
    and occupies a prominent place in the history of French literature in the 19th century.
    <br />
    "<i>My noble companions, I guard your worship;
Even banished, the Republic is there that unites us.
I will cover with glory all those who are insulted;
I will cast reproach on all those who are blessed!

I will be, under the bag of ashes that covers me,
The voice that says: woe! the mouth that says: no!
While your servants will show you your Louvre,
I will show you, Caesar, your shed.</i>"
  </Poet>

  <Poet>
    <template #icon>
      <HikmetIcon />
    </template>
    <template #heading>Nazem Hikmat</template>

    Nâzım Hikmet is one of the most important figures in Turkish literature of the 20th century, and one of the first Turkish poets to use free verse. Hikmet became, during his lifetime, 
    one of the best known Turkish poets in the West and his works have been translated into more than fifty languages. <br />

    "<i>The most beautiful sea
hasn't been crossed yet.
The most beautiful child
hasn't grown up yet.
Our most beautiful days
we haven't seen yet.
And the most beautiful words I wanted to tell you
I haven't said yet</i>"
  </Poet>

  <Poet>
    <template #icon>
      <RimbaudIcon />
    </template>
    <template #heading>Arthur Rimbaud</template>

    
He is a French poet, born October 20, 1854 and died November 10, 1891. Although brief, his poetic work is characterized 
by a prodigious thematic and stylistic density, making him one of the major figures of French literature. <br />
"<i>
Perfumes do not make his nostrils shiver;
He sleeps in the sun, his hand on his chest,
Calm. There are two red holes on the right side.</i>"
  </Poet>

  <Poet>
    <template #icon>
      <AntarIcon />
    </template>
    <template #heading>Antar Ben Chadad</template>

    He is one of the greatest arabic medieval poets. One of its poems was hung on the Kaaba to signify its great quality.
    He was also the knigth protectro of his tribe and was famous for his courage.
    "<i>Oh my dear,
ask those who are witnesses,
They will tell you that I am not afraid of war,
But I flee at the hour of spoils.
I though of you
as the arrows fell,
And the spearheads of my blood are soaked.
So I wanted to kiss these swords,
because they shone with the whiteness of your smiling mouth.</i>"
  </Poet>
</template>
